---
title: Solucionando problemas de manipuladores de eventos herdados no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: f2ddef64ca02ca7c96c6c906f5ee79e3cf99dece
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604058"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Solucionando problemas de manipuladores de eventos herdados no Visual Basic
Este tópico lista problemas comuns que surgem com manipuladores de eventos em componentes herdados.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Código no manipulador de eventos é executado duas vezes para cada chamada  
  
- Um manipulador de eventos herdados não deve incluir um [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula. O método na classe base já está associado ao evento e será acionado adequadamente. Remover o `Handles` cláusula do método herdado.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Se o método herdado não tem um `Handles` palavra-chave, verifique se que seu código não contém um extra [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou todos os métodos adicionais que lidar com o mesmo evento.  
  
## <a name="see-also"></a>Consulte também

- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
