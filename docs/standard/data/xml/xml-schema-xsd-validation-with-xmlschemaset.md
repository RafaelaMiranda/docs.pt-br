---
title: Validação de XSD (esquema XML) com XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bdcfe785d6f5f81d721acd45eebb580b08b2d14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916073"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Validação de XSD (esquema XML) com XmlSchemaSet
Documentos XML podem ser validados em um esquema da linguagem XSD em um <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Validando documentos XML  
 Documentos XML são validados pelo método <xref:System.Xml.XmlReader.Create%2A> da classe <xref:System.Xml.XmlReader>. Para validar um documento XML, construa um objeto <xref:System.Xml.XmlReaderSettings> que contém uma linguagem XSD com a qual validar o documento XML.  
  
> [!NOTE]
> O namespace <xref:System.Xml.Schema> contém métodos de extensão que facilitam a validação de uma árvore XML em um arquivo XSD ao usar [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) e [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Para obter mais informações sobre como validar documentos XML com o LINQ to XML, confira [Como: validar usando XSD (LINQ to XML) (C#)](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) e [Como: validar usando XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).  
  
 Um esquema individual ou um conjunto de esquemas (como <xref:System.Xml.Schema.XmlSchemaSet>) podem ser adicionados a um <xref:System.Xml.Schema.XmlSchemaSet> passando qualquer um como um parâmetro para o método <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>. Observe que, ao validar um documento, o namespace de destino do documento deve corresponder ao namespace de destino do esquema no conjunto de esquema.  
  
 Veja a seguir um documento XML de exemplo.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Veja a seguir o esquema que valida o documento XML de exemplo.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 No exemplo de código a seguir, o esquema acima é adicionado à propriedade <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> do objeto <xref:System.Xml.XmlReaderSettings>. O objeto <xref:System.Xml.XmlReaderSettings> é passado como um parâmetro para o método <xref:System.Xml.XmlReader.Create%2A> do objeto <xref:System.Xml.XmlReader>, que valida o documento XML acima.  
  
 A propriedade <xref:System.Xml.XmlReaderSettings.ValidationType%2A> do objeto <xref:System.Xml.XmlReaderSettings> é definida como `Schema` para aplicar a validação o documento XML pelo método <xref:System.Xml.XmlReader.Create%2A> do objeto <xref:System.Xml.XmlReader>. Um <xref:System.Xml.Schema.ValidationEventHandler> é adicionado ao objeto <xref:System.Xml.XmlReaderSettings> para manipular qualquer evento <xref:System.Xml.Schema.XmlSeverityType.Warning> ou <xref:System.Xml.Schema.XmlSeverityType.Error> gerado por erros encontrados durante o processo de validação do documento XML e do esquema.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [XmlSchemaSet para compilação de esquema](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Trabalhando com esquemas XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
