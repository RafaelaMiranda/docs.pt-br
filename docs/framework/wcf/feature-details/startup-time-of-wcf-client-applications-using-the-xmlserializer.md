---
title: 'Como: melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: f8766a5dfa2bcfc715a0f0e21274f7c6ac04ad15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944890"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Como: melhorar o tempo de inicialização dos aplicativos do cliente WCF usando o XmlSerializer
Os serviços e os aplicativos cliente que usam tipos de dados que são serializados usando <xref:System.Xml.Serialization.XmlSerializer> geram e compilam o código de serialização para esses tipos de dados em tempo de execução, o que pode levar a um desempenho de inicialização lento.  
  
> [!NOTE]
> O código de serialização pré-gerado somente pode ser usado em aplicativos cliente e não em serviços.  
  
 A [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode melhorar o desempenho de inicialização para esses aplicativos, gerando o código de serialização necessário dos assemblies compilados para o aplicativo. Svcutil. exe gera código de serialização para todos os tipos de dados usados em contratos de serviço no assembly de aplicativo compilado que pode <xref:System.Xml.Serialization.XmlSerializer>ser serializado usando o. Os contratos de serviço e operação que <xref:System.Xml.Serialization.XmlSerializer> usam o são marcados <xref:System.ServiceModel.XmlSerializerFormatAttribute>com o.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Para gerar o código de serialização XmlSerializer  
  
1. Compile o código do cliente ou do serviço em um ou mais assemblies.  
  
2. Abra um prompt de comando do SDK.  
  
3. No prompt de comando, inicie a ferramenta svcutil. exe usando o formato a seguir.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     O `assemblyPath` argumento especifica o caminho para um assembly que contém tipos de contrato de serviço. Svcutil. exe gera código de serialização para todos os tipos de dados usados em contratos de serviço no assembly de aplicativo compilado que pode <xref:System.Xml.Serialization.XmlSerializer>ser serializado usando o.  
  
     Svcutil. exe só pode gerar C# código de serialização. Um arquivo de código-fonte é gerado para cada assembly de entrada. Você não pode usar a opção **/Language** para alterar o idioma do código gerado.  
  
     Para especificar o caminho para assemblies dependentes, use a opção **/Reference** .  
  
4. Torne o código de serialização gerado disponível para seu aplicativo usando uma das seguintes opções:  
  
    1. Compile o código de serialização gerado em um assembly separado com o nome [*assembly original*]. XmlSerializer. dll (por exemplo, MyApp. XmlSerializer. dll). Seu aplicativo deve ser capaz de carregar o assembly, que deve ser assinado com a mesma chave que o assembly original. Se você recompilar o assembly original, deverá regenerar o assembly de serialização.  
  
    2. Compile o código de serialização gerado em um assembly separado e use <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> o no contrato de serviço que usa <xref:System.ServiceModel.XmlSerializerFormatAttribute>o. Defina as <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> propriedades <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> ou para apontar para o assembly de serialização compilado.  
  
    3. Compile o código de serialização gerado em seu assembly de aplicativo e <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> adicione o ao contrato de serviço que <xref:System.ServiceModel.XmlSerializerFormatAttribute>usa o. Não defina as <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> Propriedades ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> . Assume-se que o assembly de serialização padrão seja o assembly atual.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Para gerar o código de serialização XmlSerializer no Visual Studio  
  
1. Crie os projetos de cliente e serviço WCF no Visual Studio. Em seguida, adicione uma referência de serviço ao projeto do cliente.  
  
2. Adicione um <xref:System.ServiceModel.XmlSerializerFormatAttribute> ao contrato de serviço no arquivo *Reference.cs* no projeto de aplicativo cliente em perreference -> **Reference. svcmap**. Observe que você precisa mostrar todos os arquivos em **Gerenciador de soluções** para ver esses arquivos.  
  
3. Crie o aplicativo cliente.  
  
4. Use a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para criar um arquivo serializador *. cs* gerado previamente usando o comando:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     O argumento assemblyPath especifica o caminho para o assembly do cliente WCF.  
  
     Como:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     O arquivo *WCFClient.XmlSerializers.dll.cs* será gerado.  
  
5. Compile o assembly de serialização gerado previamente.  
  
     Com base no exemplo na etapa anterior, o comando Compile seria o seguinte:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Verifique se o *WCFClient. XmlSerializer. dll* gerado está no mesmo diretório que o aplicativo cliente, que é *WCFClient. exe* nesse caso.  
  
6. Execute o aplicativo cliente como de costume. O assembly de serialização gerado previamente será usado.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir gera tipos de `XmlSerializer` serialização para tipos que qualquer serviço de contrato no assembly usa.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Consulte também

- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
