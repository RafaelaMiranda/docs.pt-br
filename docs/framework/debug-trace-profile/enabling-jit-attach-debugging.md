---
title: Habilitando a depuração por anexação JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052834"
---
# <a name="enabling-jit-attach-debugging"></a>Habilitando a depuração por anexação JIT
A depuração de anexação JIT é a expressão usada para descrever a anexação de um depurador a um processo quando você encontra erros ou ela pode ser disparada por funções ou métodos específicos.  
  
 A depuração de anexação JIT é usada nas seguintes condições de falha:  
  
- Exceções sem tratamento (no código nativo e gerenciado).  
  
- Método <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> ou função [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) (família Windows 7).  
  
- Erros fatais de tempo de execução.  
  
 A depuração de anexação JIT também é disparada por chamadas às seguintes funções e métodos:  
  
- Método <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>.  
  
- Método <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>.  
  
- Função [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) (Win32).  
  
 Antes do .NET Framework 4, o .NET Framework forneceu chaves de registro separadas para controlar o comportamento de depuradores nativos e gerenciados. A partir do .NET Framework 4, o controle é consolidado em uma única chave do registro: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Os valores que podem ser definidos para essa chave determinam se um depurador é invocado e, nesse caso, se ele é invocado com uma caixa de diálogo que exige a interação do usuário. Para obter informações sobre como definir essa chave do registro, consulte [Configurando a depuração automática](https://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Consulte também

- [Depuração, rastreamento e criação de perfil](index.md)
- [Facilitando a depuração de uma imagem](making-an-image-easier-to-debug.md)
