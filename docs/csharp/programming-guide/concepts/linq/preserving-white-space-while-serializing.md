---
title: Preservar espaço em branco ao serializar3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484080"
---
# <a name="preserving-white-space-while-serializing"></a>Preservar espaço em branco para serializar
Este tópico descreve como controlar o espaço em branco para serializar uma árvore XML.  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados. Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Você pode não querer modificar este recuo de nenhuma forma. Para fazer isso em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Comportamento de espaço em branco de métodos que serializam árvores XML  
 Os seguintes métodos nas classes de <xref:System.Xml.Linq.XElement> e de <xref:System.Xml.Linq.XDocument> serialize uma árvore XML. Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>. O método de `ToString` serializa a uma cadeia de caracteres.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Se o método não utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, o método irá formatar (corte XML serializável.) Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.  
  
 Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, então você pode especificar que o formato de método não (corte XML serializável.) Nesse caso, qualquer espaço em branco na árvore XML é preservada.  
