---
title: Evento ETW Exception Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91abd9e6f31380b7e8cd3df1a14aa5c5722901ba
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046509"
---
# <a name="exception-thrown_v1-etw-event"></a>Evento ETW Exception Thrown_V1
Esse evento captura informações sobre as exceções geradas.  
  
 A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Aviso (2)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Uma exceção gerenciada é gerada.|  
  
 A tabela a seguir mostra dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Tipo de exceção|win:UnicodeString|Tipo da exceção; por exemplo, `System.NullReferenceException`.|  
|Mensagem de exceção|win:UnicodeString|A mensagem de exceção real.|  
|EIPCodeThrow|win:Pointer|Ponteiro de instrução em que ocorreu a exceção.|  
|ExceptionHR|win:UInt32|Exceção [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|win:UInt16|0x01: HasInnerException (consulte [eventos de ETW do CLR](clr-etw-events.md) na documentação do Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [tratamento de exceções de estado corrompido](https://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).<br /><br /> 0x10: IsCLSCompliant (uma exceção derivada de <xref:System.Exception> é compatível com CLS; caso contrário, não é compatível com CLS).|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
## <a name="see-also"></a>Consulte também

- [Eventos de CLR ETW](clr-etw-events.md)
