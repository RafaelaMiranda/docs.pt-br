---
title: Este aplicativo de instância única não pôde se conectar à instância original
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 5585da7f2ccf7d5d3ec8db281ab9534249020a63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619843"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Este aplicativo de instância única não pôde se conectar à instância original
Este aplicativo de instância única não pôde se conectar à instância original. Algumas das possíveis causas para esse problema são as seguintes:  
  
- A instância original parou de responder.  
  
- O aplicativo não tem permissões para criar objetos kernel. Para obter mais informações sobre objetos kernel, consulte [Mutexes](../../standard/threading/mutexes.md).  
  
     O nome de base para os objetos kernel vem da concatenação do GUID do assembly, número da versão principal e número da versão secundária. Por exemplo, o nome de base pode ser `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Para corrigir esse erro ao desenvolver o aplicativo  
  
1. Verifique se o aplicativo não entrar em um estado sem resposta.  
  
2. Verifique se o aplicativo tem permissões suficientes para criar objetos kernel.  
  
3. Reinicie a instância original do aplicativo.  
  
4. Reinicie o computador para limpar qualquer processo que possam estar usando o recurso que é necessário para se conectar ao aplicativo da instância original.  
  
5. Observe as circunstâncias sob as quais o erro ocorreu e telefone o Microsoft Product Support Services.  
  
## <a name="see-also"></a>Consulte também

- [Noções básicas do depurador](/visualstudio/debugger/debugger-basics)
