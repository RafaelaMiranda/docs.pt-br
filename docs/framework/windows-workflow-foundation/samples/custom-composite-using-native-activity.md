---
title: Atividade nativo de usar composta personalizada
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 8a0d1077c058ecdbad10a2e7bd61ff5eb75e1cb5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044316"
---
# <a name="custom-composite-using-native-activity"></a>Atividade nativo de usar composta personalizada
Este exemplo demonstra como escrever <xref:System.Activities.NativeActivity> que agenda outros objetos de <xref:System.Activities.Activity> para controlar o fluxo de execução de um fluxo de trabalho. Este exemplo usar dois fluxos comuns de controle, e quando sequência, para demonstrar como fazer isso.

## <a name="sample-details"></a>Detalhes de exemplo
 Iniciando com `MySequence`, a primeira coisa para observar que é derivada de <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> é o objeto de <xref:System.Activities.Activity> que expõe a largura total de fluxo de trabalho com <xref:System.Activities.NativeActivityContext> passado para o método de `Execute` .

 `MySequence` expõe uma coleção pública de objetos <xref:System.Activities.Activity> que obtém preenchido pelo autor de fluxo de trabalho. Antes que o fluxo de trabalho é executado, o tempo de execução de fluxo de trabalho chama o método de <xref:System.Activities.Activity.CacheMetadata%2A> em cada atividade em um fluxo de trabalho. Durante esse processo, o tempo de execução estabelecer relações pai-filho para o escopo de dados e o gerenciamento de tempo de vida. A implementação <xref:System.Activities.Activity.CacheMetadata%2A> padrão do método usa a <xref:System.ComponentModel.TypeDescriptor> classe `MySequence` de instância da atividade para adicionar qualquer propriedade pública do tipo <xref:System.Activities.Activity> ou <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity>> como filhos do `MySequence` atividade.

 Sempre que uma atividade expõe uma coleção pública de atividades filhos, é provável estado filho de compartilhamento dessas atividades. É uma prática recomendada para atividades pai, nesse caso `MySequence`, também expor uma coleção de variáveis com que as atividades filho podem fazer isso. Como as atividades filhas, <xref:System.Activities.Activity.CacheMetadata%2A> o método adiciona propriedades públicas do <xref:System.Activities.Variable> tipo <xref:System.Collections.IEnumerable>ou \< <xref:System.Activities.Variable>> como variáveis associadas `MySequence` à atividade.

 Além de variáveis públicas, que são manipulados pelos filhos de `MySequence`, `MySequence` também deve manter controle de onde está em execução de seus filhos. Usa uma variável particular, `currentIndex`, para fazer isso. Esta variável é registrado como parte do ambiente de `MySequence` adicionando uma chamada para o método de <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> no método de `MySequence` de atividade de <xref:System.Activities.Activity.CacheMetadata%2A> . Os <xref:System.Activities.Activity> objetos `MySequence` adicionados`Activities` à coleção não podem acessar variáveis adicionadas dessa maneira.

 Quando `MySequence` é executado em tempo de execução, o tempo de execução chama o método de <xref:System.Activities.NativeActivity.Execute%2A> , passando <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> é o proxy de atividade de novo em tempo de execução para desreferenciar argumentos e variáveis bem como agendar outros objetos de <xref:System.Activities.Activity> , ou `ActivityDelegates`. `MySequence` usa um método de `InternalExecute` para encapsular a lógica de agendar o primeiro filho e todos os filhos subsequentes em um único método. Inicia desreferenciando `currentIndex`. Se for igual a contagem na coleção de `Activities` , então a sequência está concluída, a atividade retorna agendar sem qualquer trabalho e o tempo de execução movê-lo no estado de <xref:System.Activities.ActivityInstanceState.Closed> . Se o `currentIndex` for menor que a contagem de atividades, o próximo filho será obtido `Activities` da coleção e `MySequence` das chamadas <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, passando o filho a ser agendado e um <xref:System.Activities.CompletionCallback> apontado para o `InternalExecute` forma. Finalmente, `currentIndex` é incrementado e o controle é rendido de volta para o tempo de execução. Como uma instância de `MySequence` tem um objeto filho de <xref:System.Activities.Activity> agendada, o tempo de execução considera-o estar no estado executando.

 Quando a atividade filho termina, <xref:System.Activities.CompletionCallback> é executado. O loop continua a parte superior. Como `Execute`, <xref:System.Activities.CompletionCallback> leva <xref:System.Activities.NativeActivityContext>, fornecendo acesso do implementador em tempo de execução.

 `MyWhile`difere de `MySequence` em que ele agenda um único <xref:System.Activities.Activity> objeto repetidamente e, em que ele usa um <xref:System.Activities.Activity%601>< bool\> chamado `Condition` para determinar se esse agendamento deve ocorrer. Como `MySequence`, `MyWhile` usa um método de `InternalExecute` para centralizar sua lógica de programação. Ele agenda o `Condition` <xref:System.Activities.Activity>< bool\> com um <xref:System.Activities.CompletionCallback%601>>boolchamado `OnEvaluationCompleted`. \< Quando a execução de `Condition` é concluída, o resultado fica disponível com esse <xref:System.Activities.CompletionCallback> em um parâmetro fortemente tipado chamado `result`. Se `true`, `MyWhile` chama o <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, passando o objeto e em `Body` de <xref:System.Activities.Activity>`InternalExecute` como <xref:System.Activities.CompletionCallback>. Quando a execução de `Body` terminar, `Condition` obtém agendada novamente em `InternalExecute`, iniciar o loop sobre novamente. Quando `Condition` retorna `false`, uma instância de `MyWhile` fornece o controle de volta para o tempo de execução sem agendar `Body` e o tempo de execução movê-lo ao estado de <xref:System.Activities.ActivityInstanceState.Closed> .

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Abra a solução de exemplo Composite. sln no Visual Studio 2010.

2. Criar e executar a solução.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
