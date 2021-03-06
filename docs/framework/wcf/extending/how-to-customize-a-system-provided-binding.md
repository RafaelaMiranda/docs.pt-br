---
title: 'Como: personalizar uma associação fornecida pelo sistema'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 6b92382b4a37168c33f9e97077ad292d27ea5bc3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797015"
---
# <a name="how-to-customize-a-system-provided-binding"></a>Como: personalizar uma associação fornecida pelo sistema
O Windows Communication Foundation (WCF) inclui várias associações fornecidas pelo sistema que permitem que você configure algumas das propriedades dos elementos de associação subjacentes, mas não todas as propriedades. Este tópico demonstra como definir propriedades nos elementos de associação para criar uma associação personalizada.  
  
 Para obter mais informações sobre como criar e configurar diretamente elementos de associação sem usar as associações fornecidas pelo sistema, consulte [associações personalizadas](custom-bindings.md).  
  
 Para obter mais informações sobre como criar e estender associações personalizadas, consulte [estendendo associações](extending-bindings.md).  
  
 No WCF, todas as associações são feitas de *elementos de associação*. Cada elemento de ligação deriva da <xref:System.ServiceModel.Channels.BindingElement> classe. Associações fornecidas pelo sistema, <xref:System.ServiceModel.BasicHttpBinding> como criar e configurar seus próprios elementos de ligação. Este tópico mostra como acessar e alterar as propriedades desses elementos de ligação, que não são expostos diretamente na associação; especificamente, a <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Os elementos de associação individuais estão contidos em uma coleção representada pela <xref:System.ServiceModel.Channels.BindingElementCollection> classe e são adicionados nesta ordem: Fluxo de transações, sessão confiável, segurança, duplex composto, unidirecional, segurança de fluxo, codificação de mensagem e transporte. Observe que nem todos os elementos de associação listados são necessários em cada associação. Elementos de associação definidos pelo usuário também podem aparecer nessa coleção de elementos de associação e devem aparecer na mesma ordem descrita anteriormente. Por exemplo, um transporte definido pelo usuário deve ser o último elemento da coleção de elementos de associação.  
  
 A <xref:System.ServiceModel.BasicHttpBinding> classe contém três elementos de ligação:  
  
1. Um elemento de associação de segurança opcional, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> a classe usada com o transporte http (segurança de nível de mensagem <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> ) ou a classe, que é usada quando a camada de transporte fornece segurança; nesse caso, o transporte HTTPS é usado.  
  
2. Um elemento de associação de codificador de <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> mensagem <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>necessário, ou.  
  
3. Um elemento de associação de transporte necessário <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, ou <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 Neste exemplo, criamos uma instância da associação, geramos uma *associação personalizada* a partir dela, examinamos os elementos de associação na associação personalizada e quando encontramos o elemento de associação http, definimos `KeepAliveEnabled` sua propriedade `false`como. A `KeepAliveEnabled` propriedade não é exposta diretamente `BasicHttpBinding`no, portanto, devemos criar uma associação personalizada para navegar até o elemento Binding e definir essa propriedade.  
  
### <a name="to-modify-a-system-provided-binding"></a>Para modificar uma associação fornecida pelo sistema  
  
1. Crie uma instância da <xref:System.ServiceModel.BasicHttpBinding> classe e defina seu modo de segurança como nível de mensagem.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. Crie uma associação personalizada da associação e crie uma <xref:System.ServiceModel.Channels.BindingElementCollection> classe a partir de uma das propriedades da associação personalizada.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. Faça um loop <xref:System.ServiceModel.Channels.BindingElementCollection> pela classe e, quando você encontrar <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a classe, defina <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> sua propriedade `false`como.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Associações personalizadas](custom-bindings.md)
