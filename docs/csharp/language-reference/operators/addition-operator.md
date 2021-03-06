---
title: + Operadores e += – referência de C#
ms.custom: seodec18
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 41355dbadd566648b45d825cdd6515bfc6d411aa
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610031"
---
# <a name="-and--operators-c-reference"></a>Operadores + e += (referência de C#)

O operador `+` é compatível com os tipos numéricos internos, o tipo [cadeia de caracteres](../keywords/string.md) e o tipo [delegado](../keywords/delegate.md).

Para obter informações sobre o operador `+` aritmético, consulte as seções [Operadores de adição e subtração unários](arithmetic-operators.md#unary-plus-and-minus-operators) e [Operador de adição +](arithmetic-operators.md#addition-operator-) do artigo [Operadores aritméticos](arithmetic-operators.md).

## <a name="string-concatenation"></a>Concatenação de cadeia de caracteres

Quando um ou os dois operandos forem do tipo [cadeia de caracteres](../keywords/string.md), o operador `+` concatenará as representações de cadeia de caracteres de seus operandos:

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

Começando com C# 6, [interpolação de cadeia de caracteres](../tokens/interpolated.md) oferece uma maneira mais conveniente de formatar cadeias de caracteres:

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Combinação de delegados

Para operandos do mesmo tipo [delegado](../keywords/delegate.md), o operador `+` retorna uma nova instância de delegado que, quando invocada, chama o operando esquerdo e, em seguida, chama o operando direito. Se qualquer um dos operandos for `null`, o operador `+` retornará o valor de outro operando (que também pode ser `null`). O exemplo a seguir mostra como os delegados podem ser combinados com o operador `+`:

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Para executar a remoção de delegado, use o [operador `-`](subtraction-operator.md#delegate-removal).

Para obter mais informações sobre tipos de delegado, veja [Delegados](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Operador de atribuição de adição +=

Uma expressão que usa o operador `+=`, como

```csharp
x += y
```

equivale a

```csharp
x = x + y
```

exceto que `x` é avaliado apenas uma vez.
  
O exemplo a seguir demonstra o uso do operador `+=`:

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Você também usará o operador `+=` para especificar um método de manipulador de eventos ao assinar um [evento](../keywords/event.md). Para obter mais informações, confira [Como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) o operador `+`. Quando um operador `+` binário é sobrecarregado, o operador `+=` também é implicitamente sobrecarregado. Um tipo definido pelo usuário não pode sobrecarregar explicitamente o operador `+=`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja as seções [Operador de adição unário](~/_csharplang/spec/expressions.md#unary-plus-operator) e [Operador de adição](~/_csharplang/spec/expressions.md#addition-operator) da [Especificação de linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Interpolação de cadeia de caracteres](../tokens/interpolated.md)
- [Como concatenar várias cadeias de caracteres](../../how-to/concatenate-multiple-strings.md)
- [Delegados](../../programming-guide/delegates/index.md)
- [Eventos](../../programming-guide/events/index.md)
- [Operadores aritméticos](arithmetic-operators.md)
- [Operadores - e -=](subtraction-operator.md)
