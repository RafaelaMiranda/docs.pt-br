---
title: Invocando um Controle Utilizando Automação de IU
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923731"
---
# <a name="invoke-a-control-using-ui-automation"></a>Invocando um Controle Utilizando Automação de IU
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico demonstra como executar as seguintes tarefas:  
  
- Localize um controle que corresponda a condições de propriedade específicas percorrendo a exibição de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controle da árvore para o aplicativo de destino.  
  
- Crie um <xref:System.Windows.Automation.AutomationElement> para cada controle.  
  
- Obtenha um <xref:System.Windows.Automation.InvokePattern> objeto de qualquer [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elemento encontrado que dê suporte <xref:System.Windows.Automation.InvokePattern> ao padrão de controle.  
  
- Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> para invocar o controle de um manipulador de eventos de cliente.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> método <xref:System.Windows.Automation.AutomationElement> da classe para gerar um <xref:System.Windows.Automation.InvokePattern> objeto e invocar um controle usando o <xref:System.Windows.Automation.InvokePattern.Invoke%2A> método.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplo de InvokePattern, ExpandCollapsePattern e TogglePattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
