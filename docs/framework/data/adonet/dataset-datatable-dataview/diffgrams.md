---
title: DiffGrams
ms.date: 03/30/2017
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
ms.openlocfilehash: dd70c8d238ba47744eec6ab4a4c6bc1e80a3d0b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784659"
---
# <a name="diffgrams"></a>DiffGrams
Um DiffGram é um formato XML que identifica as versões atuais e originais dos elementos de dados. O <xref:System.Data.DataSet> usa o formato DiffGram para carregar e manter seu conteúdo e para serializar seu conteúdo para transporte em uma conexão de rede. Quando um <xref:System.Data.DataSet> é escrito como um DiffGram, ele popula o DiffGram com todas as informações necessárias para recriar com precisão o conteúdo, embora não seja o esquema, <xref:System.Data.DataSet>do, incluindo valores de coluna do **original** e **do** Versões de linha atuais, informações de erro de linha e ordem de linha.  
  
 Ao enviar e recuperar um <xref:System.Data.DataSet> de um serviço Web XML, o formato DiffGram é usado implicitamente. Além disso, ao carregar o conteúdo de <xref:System.Data.DataSet> um XML usando o método **ReadXml** ou ao gravar o conteúdo de um <xref:System.Data.DataSet> em XML usando o método **WriteXml** , você pode especificar que o conteúdo seja lido ou gravado como um DiffGram. Para obter mais informações, consulte [carregando um conjunto de dados a partir de XML](loading-a-dataset-from-xml.md) e [gravando conteúdo do DataSet como XML](writing-dataset-contents-as-xml-data.md).  
  
 Embora o formato DiffGram seja usado principalmente pelo .NET Framework como um formato de serialização para o conteúdo de um <xref:System.Data.DataSet>, você também pode usar DiffGrams para modificar dados em tabelas em um banco de dados Microsoft SQL Server.  
  
 Um DiffGram é gerado pela gravação do conteúdo de todas as tabelas em um  **\<elemento > DiffGram** .  
  
### <a name="to-generate-a-diffgram"></a>Para gerar um DiffGram  
  
1. Gerar uma lista de tabelas raiz (ou seja, tabelas sem qualquer pai).  
  
2. Para cada tabela e seus descendentes na lista, anote a versão atual de todas as linhas na primeira seção DiffGram.  
  
3. Para cada tabela no <xref:System.Data.DataSet>, anote a versão original de todas as linhas, se houver,  **\<** na seção antes de > do DiffGram.  
  
4. Para linhas com erros, grave o conteúdo de erro na  **\<seção erros >** do DiffGram.  
  
 Um DiffGram é processado na ordem do início do arquivo XML até o fim.  
  
### <a name="to-process-a-diffgram"></a>Para processar um DiffGram  
  
1. Processar a primeira seção do DiffGram que contém a versão atual das linhas.  
  
2. Processe a segunda ou a  **\<seção anterior >** que contém a versão de linha original das linhas modificadas e excluídas.  
  
    > [!NOTE]
    > Se uma linha for marcada como excluída, a operação de exclusão também poderá excluir os descendentes da linha, dependendo da `Cascade` Propriedade do atual. <xref:System.Data.DataSet>  
  
3. Processe a  **\<seção erros >** . Defina as informações de erro para a linha e a coluna especificadas para cada item nesta seção.  
  
> [!NOTE]
> Se você definir <xref:System.Data.XmlWriteMode> como DiffGram, o conteúdo do destino <xref:System.Data.DataSet> e o original <xref:System.Data.DataSet> poderão ser diferentes.  
  
## <a name="diffgram-format"></a>Formato DiffGram  
 O formato DiffGram é dividido em três seções: os dados atuais, os dados originais (ou "anteriores") e uma seção de erros, conforme mostrado no exemplo a seguir.  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 O formato DiffGram consiste nos seguintes blocos de dados:  
  
 **\<**  ***DataInstance***  **>**  
 O nome desse elemento, ***DataInstance***, é usado para fins explicativos nesta documentação. Um elemento ***DataInstance*** representa uma <xref:System.Data.DataSet> ou uma linha de um <xref:System.Data.DataTable>. Em vez de *DataInstance*, o elemento conterá o nome do <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>. Esse bloco do formato DiffGram contém os dados atuais, se eles foram modificados ou não. Um elemento, ou linha, que foi modificado, é identificado com a anotação **diffgr: hasChanges** .  
  
 **\<diffgr:before>**  
 Esse bloco do formato DiffGram contém a versão original de uma linha. Os elementos neste bloco são correspondidos aos elementos no bloco ***DataInstance*** usando a anotação **diffgr: ID** .  
  
 **\<diffgr:errors>**  
 Esse bloco do formato DiffGram contém informações de erro para uma linha específica no bloco ***DataInstance*** . Os elementos neste bloco são correspondidos aos elementos no bloco ***DataInstance*** usando a anotação **diffgr: ID** .  
  
## <a name="diffgram-annotations"></a>Anotações de DiffGram  
 Os DiffGrams usam várias anotações para relacionar os elementos dos diferentes blocos de DiffGram que representam diferentes versões de linha ou informações <xref:System.Data.DataSet>de erro no.  
  
 A tabela a seguir descreve as anotações de DiffGram que são definidas no namespace do DiffGram **urn: schemas-microsoft-com: XML-DiffGram-v1**.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**id**|Usado para emparelhar os elementos em  **\<diffgr: Before >** **\<** e  **\<diffgr: erros >** blocos para elementos no bloco ***DataInstance*** **>** . Os valores com a anotação **diffgr: ID** estão no formato *[TableName] [ID do @ identificador]* . Por exemplo: `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identifica qual elemento do **\<** bloco ***DataInstance*** **>** é o elemento pai do elemento atual. Os valores com a anotação **diffgr: parentID** estão no formato *[TableName] [ID do @ identificador]* . Por exemplo: `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifica uma linha no **\<** bloco ***DataInstance*** **>** como modificada. A anotação **HasChanges** pode ter um dos dois valores a seguir:<br /><br /> **inserted**<br /> Identifica uma linha **adicionada** .<br /><br /> **alteração**<br /> Identifica uma linha **modificada** que contém uma  **\<** versão de linha original no bloco diffgr: Before >. Observe que as linhas **\<** **excluídas** terão uma **>**  **\<** versão de linha original no bloco diffgr: Before >, mas não haverá nenhum elemento anotado no bloco DataInstance.|  
|**hasErrors**|Identifica uma linha **\<** no bloco ***DataInstance*** **>** com um rowgroup. O elemento error é colocado no  **\<bloco diffgr: Errors >** .|  
|**Erro**|Contém o texto do **usererror** para um elemento específico no  **\<bloco diffgr: Errors >** .|  
  
 O <xref:System.Data.DataSet> inclui anotações adicionais ao ler ou gravar seu conteúdo como um DiffGram. A tabela a seguir descreve essas anotações adicionais, que são definidas no namespace **urn: schemas-microsoft-com: xml-msdata**.  
  
|Anotação|Descrição|  
|----------------|-----------------|  
|**RowOrder**|Preserva a ordem de linha dos dados originais e identifica o índice de uma linha em um determinado <xref:System.Data.DataTable>.|  
|**Oculto**|Identifica uma coluna como tendo uma propriedade **ColumnMapping** definida como **MappingType. Hidden**. O atributo é escrito no formato **MSDATA: Hidden** *[ColumnName]* = "*Value*". Por exemplo: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Observe que as colunas ocultas só serão gravadas como um atributo DiffGram se eles contiverem dados. Caso contrário, eles serão ignorados.|  
  
## <a name="sample-diffgram"></a>DiffGram de exemplo  
 Um exemplo do formato DiffGram é mostrado abaixo. Este exemplo mostra o resultado de uma atualização para uma linha em uma tabela antes que as alterações sejam confirmadas. A linha com um CustomerID de "ALFKI" foi modificada, mas não foi atualizada. Como resultado, há uma linha **atual** com um **diffgr: ID** de **\<** "Customers1" no bloco ***DataInstance*** **>** e uma linha **original** com um **diffgr: ID** de "Customers1" no  **\< diffgr: antes** do bloco de >. A linha com um CustomerID de "ANATR" inclui um **rowgroup, portanto**, é anotada `diffgr:hasErrors="true"` e há um elemento  **\<relacionado no bloco diffgr: Errors >** .  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a>Consulte também

- [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet)
- [Carregar um conjunto de dados do XML](loading-a-dataset-from-xml.md)
- [Gravar o conteúdo do conjunto de dados como dados XML](writing-dataset-contents-as-xml-data.md)
- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
