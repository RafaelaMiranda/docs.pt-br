---
title: Executando operações aritméticas com datas e horários
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01314c160fc531f5c97a1369c8444dce7f590d53
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106609"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Executando operações aritméticas com datas e horários

Embora tanto o <xref:System.DateTime> quanto as <xref:System.DateTimeOffset> estruturas forneçam Membros que executam operações aritméticas em seus valores, os resultados de operações aritméticas são muito diferentes. Este tópico examina essas diferenças, relaciona-as a graus de reconhecimento de fuso horário em dados de data e hora e discute como executar operações de reconhecimento de fuso horário integralmente usando dados de data e hora.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Comparações e operações aritméticas com valores DateTime

A <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriedade permite que <xref:System.DateTimeKind> um valor seja atribuído à data e hora para indicar se ela representa a hora local, UTC (tempo Universal Coordenado) ou a hora em um fuso horário não especificado. No entanto, essas informações limitadas de fuso horário são ignoradas ao comparar ou executar <xref:System.DateTimeKind> a aritmética de data e hora em valores. O exemplo a seguir, que compara o horário local atual com o horário UTC atual, ilustra isso.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

O <xref:System.DateTime.CompareTo%28System.DateTime%29> método relata que a hora local é anterior a (ou menor que) a hora UTC, e a operação de subtração indica que a diferença entre o UTC e a hora local de um sistema nos EUA Pacífico dos EUA é de sete horas. Porém, como esses dois valores oferecem representações diferentes de um único momento, fica claro que, nesse caso, o intervalo de tempo é completamente atribuível ao deslocamento do fuso horário local em relação ao UTC.

Em geral, a <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriedade não afeta os resultados retornados por <xref:System.DateTime.Kind> métodos de comparação e aritméticos (já que a comparação de dois pontos idênticos no tempo indica), embora possa afetar a interpretação desses resultados. Por exemplo:

- O resultado de qualquer operação aritmética executada em dois valores de data e hora <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> cujas propriedades são <xref:System.DateTimeKind> iguais refletem o intervalo de tempo real entre os dois valores. Da mesma forma, a comparação dos dois valores de data e hora reflete com precisão a relação entre horários.

- O resultado de qualquer operação aritmética ou de comparação executada em dois valores de data e <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hora cujas propriedades <xref:System.DateTimeKind> são iguais ou em dois valores de data e <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> hora com valores de propriedade diferentes reflete a diferença na hora do relógio entre os dois valores.

- As operações aritméticas ou de comparação em valores de data e hora local não consideram se um valor específico é ambíguo ou inválido nem levam em conta o efeito de regras de ajuste que resultam da transição do fuso horário local de ou para o horário de verão.

- Qualquer operação que compara ou calcula a diferença entre o UTC e o horário local inclui um intervalo de tempo igual ao deslocamento do fuso horário local em relação ao UTC no resultado.

- Qualquer operação que compara ou calcula a diferença entre um horário não especificado e o UTC ou o horário local reflete a hora do relógio simples. As diferenças de fuso horário não são consideradas; o resultado não reflete a aplicação das regras de ajuste de fuso horário.

- Qualquer operação que compara ou calcula a diferença entre dois horários não especificados poderá incluir um intervalo desconhecido que reflete a diferença entre o horário em dois fusos horários diferentes.

Há muitos cenários em que as diferenças de fuso horário não afetam os cálculos de data e hora (para uma discussão sobre alguns deles, consulte [escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)) ou no qual o contexto dos dados de data e hora define o significado de operações de comparação ou aritmética.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Comparações e operações aritméticas com valores de DateTimeOffset

Um <xref:System.DateTimeOffset> valor inclui não apenas uma data e hora, mas também um deslocamento que define inequivocamente a data e a hora em relação ao UTC. Isso torna possível definir igualdade um pouco diferente do que para <xref:System.DateTimeOffset> valores. Enquanto <xref:System.DateTime> os valores são iguais se tiverem o mesmo valor de data e hora <xref:System.DateTimeOffset> , os valores serão iguais se ambos fizerem referência ao mesmo ponto no tempo. Isso torna um <xref:System.DateTimeOffset> valor mais preciso e menos preciso de interpretação quando usado em comparações e na maioria das operações aritméticas que determinam o intervalo entre duas datas e horas. O exemplo a seguir, que é <xref:System.DateTimeOffset> o equivalente ao exemplo anterior que comparava valores <xref:System.DateTimeOffset> locais e UTC, ilustra essa diferença no comportamento.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Neste exemplo, o <xref:System.DateTimeOffset.CompareTo%2A> método indica que a hora local atual e a hora UTC atual são iguais, e a subtração de <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> valores indica que a diferença entre as duas horas é. <xref:System.TimeSpan.Zero?displayProperty=nameWithType>

A principal limitação de usar <xref:System.DateTimeOffset> valores na aritmética de data e hora é que <xref:System.DateTimeOffset> , embora os valores tenham algum reconhecimento de fuso horário, eles não são totalmente cientes do fuso horário. Embora o <xref:System.DateTimeOffset> deslocamento do valor reflita um deslocamento de fuso horário do UTC quando uma <xref:System.DateTimeOffset> variável recebe primeiro um valor, ele se torna desassociado do fuso horário depois. Como não estão mais diretamente associadas a um horário identificável, a adição e a subtração dos intervalos de data e hora não consideram as regras de ajuste de um fuso horário.

Para ilustrar, a transição para o horário de verão no fuso horário padrão da região central EUA ocorre às 2h. em 9 de março de 2008. Isso significa que adicionar um intervalo de duas horas e meia ao fuso horário padrão da região central de 1h30min em 9 de março de 2008 deve produzir uma data e hora de 5h em 9 de março de 2008. No entanto, como mostra o exemplo a seguir, o resultado da adição é 4h em 9 de março de 2008. Observe que o resultado dessa operação representa o momento correto, embora não seja o horário no fuso horário em que estamos interessados (ou seja, não tem o deslocamento de fuso horário esperado).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Operações aritméticas com tempos em fusos horários

A <xref:System.TimeZoneInfo> classe inclui vários métodos de conversão que aplicam ajustes automaticamente quando convertem horários de um fuso horário para outro. Eles incluem o seguinte:

- Os <xref:System.TimeZoneInfo.ConvertTime%2A> métodos <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> e, que convertem os horários entre dois fusos horários.

- Os <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> métodos <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> e, que convertem a hora em um fuso horário específico para UTC ou convertem UTC para a hora em um fuso horário específico.

Para obter detalhes, consulte [conversão de horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md).

A <xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> classe não fornece nenhum método que aplique regras de ajuste automaticamente quando você executar aritmética de data e hora. No entanto, é possível fazer isso convertendo o horário em um fuso horário para UTC, executando a operação aritmética e, em seguida, convertendo do UTC novamente para o horário no fuso horário. Para obter detalhes, confira [Como: Use fusos horários em aritmética](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)de data e hora.

Por exemplo, o código a seguir é semelhante ao código anterior, que adicionou duas horas e meia às 2h em 9 de março de 2008. No entanto, como converte um horário padrão da região central em UTC antes de realizar a aritmética de data e hora e, depois, converte o resultado do UTC novamente no horário padrão da região central, o horário resultante reflete a transição do fuso horário padrão da região central para o horário de verão.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Como: Usar fusos horários em aritmética de data e hora](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
