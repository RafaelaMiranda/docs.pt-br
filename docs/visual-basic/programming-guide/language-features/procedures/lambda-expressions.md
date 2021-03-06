---
title: Expressões lambda (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: d3c385737d7f3a25009dba3abfffe88a1cf1619a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524052"
---
# <a name="lambda-expressions-visual-basic"></a>Expressões lambda (Visual Basic)

Uma *expressão lambda* é uma função ou sub-rotina sem um nome que pode ser usado sempre que um delegado é válido. As expressões lambda podem ser funções ou sub-rotinas e podem ser de linha única ou várias linhas. Você pode passar valores do escopo atual para uma expressão lambda.

> [!NOTE]
> A instrução `RemoveHandler` é uma exceção. Não é possível passar uma expressão lambda no para o parâmetro delegado de `RemoveHandler`.

Você cria expressões lambda usando a palavra-chave `Function` ou `Sub`, assim como cria uma função ou sub-rotina padrão. No entanto, as expressões lambda são incluídas em uma instrução.

O exemplo a seguir é uma expressão lambda que incrementa seu argumento e retorna o valor. O exemplo mostra a sintaxe de expressão lambda de linha única e de várias linhas para uma função.

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

O exemplo a seguir é uma expressão lambda que grava um valor no console. O exemplo mostra a sintaxe de expressão lambda de linha única e de várias linhas para uma sub-rotina.

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

Observe que, nos exemplos anteriores, as expressões lambda são atribuídas a um nome de variável. Sempre que você se referir à variável, invocará a expressão lambda. Você também pode declarar e invocar uma expressão lambda ao mesmo tempo, conforme mostrado no exemplo a seguir.

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

Uma expressão lambda pode ser retornada como o valor de uma chamada de função (como é mostrado no exemplo na seção de [contexto](#context) mais adiante neste tópico) ou passada como um argumento para um parâmetro que usa um tipo delegado, como mostrado no exemplo a seguir.

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>Sintaxe da expressão lambda

A sintaxe de uma expressão lambda é semelhante à de uma função padrão ou sub-rotina. As diferenças são as seguintes:

- Uma expressão lambda não tem um nome.

- Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.

- As funções lambda de linha única não usam uma cláusula `As` para designar o tipo de retorno. Em vez disso, o tipo é inferido do valor que o corpo da expressão lambda avalia. Por exemplo, se o corpo da expressão lambda for `cust.City = "London"`, seu tipo de retorno será `Boolean`.

- Em funções lambda de várias linhas, você pode especificar um tipo de retorno usando uma cláusula `As` ou omitir a cláusula `As` para que o tipo de retorno seja inferido. Quando a cláusula `As` é omitida para uma função lambda de várias linhas, o tipo de retorno é inferido para ser o tipo dominante de todas as instruções `Return` na função lambda de várias linhas. O *tipo dominante* é um tipo exclusivo para o qual todos os outros tipos podem ampliar. Se esse tipo exclusivo não puder ser determinado, o tipo dominante será o tipo exclusivo que todos os outros tipos na matriz podem restringir. Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`. Nesse caso, se `Option Strict` for definido como `On`, ocorrerá um erro do compilador.

     Por exemplo, se as expressões fornecidas para a instrução `Return` contiverem valores do tipo `Integer`, `Long` e `Double`, a matriz resultante será do tipo `Double`. Tanto `Integer` quanto `Long` se ampliam para `Double` e somente `Double`. Portanto, `Double` é o tipo dominante. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).

- O corpo de uma função de linha única deve ser uma expressão que retorne um valor, não uma instrução. Não há nenhuma instrução `Return` para funções de linha única. O valor retornado pela função de linha única é o valor da expressão no corpo da função.

- O corpo de uma sub-rotina de linha única deve ser uma instrução de linha única.

- As funções e sub-rotinas de linha única não incluem uma instrução `End Function` ou `End Sub`.

- Você pode especificar o tipo de dados de um parâmetro de expressão lambda usando a palavra-chave `As` ou o tipo de dados do parâmetro pode ser inferido. Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.

- os parâmetros `Optional` e `Paramarray` não são permitidos.

- Parâmetros genéricos não são permitidos.

## <a name="async-lambdas"></a>Lambdas assíncronos

Você pode criar facilmente expressões lambda e instruções que incorporam o processamento assíncrono usando as palavras-chave operador [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [Await](../../../../visual-basic/language-reference/operators/await-operator.md) . Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Você pode adicionar o mesmo manipulador de eventos usando um lambda assíncrono em uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [programação assíncrona com Async e Await](../../../../visual-basic/programming-guide/concepts/async/index.md).

## <a name="context"></a>Contexto

Uma expressão lambda compartilha seu contexto com o escopo no qual ele é definido. Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção. Isso inclui o acesso a variáveis de membro, funções e sub-rotinas, `Me` e parâmetros e variáveis locais no escopo de contenção.

O acesso a variáveis locais e parâmetros no escopo de contenção pode se estender além do tempo de vida desse escopo. Desde que um delegado que se refira a uma expressão lambda não esteja disponível para a coleta de lixo, o acesso às variáveis no ambiente original é mantido. No exemplo a seguir, a variável `target` é local para `makeTheGame`, o método no qual a expressão lambda `playTheGame` é definida. Observe que a expressão lambda retornada, atribuída a `takeAGuess` no `Main`, ainda tem acesso à variável local `target`.

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

O exemplo a seguir demonstra a ampla variedade de direitos de acesso da expressão lambda aninhada. Quando a expressão lambda retornada é executada a partir de `Main` como `aDel`, ela acessa esses elementos:

- Um campo da classe na qual está definido: `aField`

- Uma propriedade da classe na qual ela está definida: `aProp`

- Um parâmetro do método `functionWithNestedLambda`, no qual ele é definido: `level1`

- Uma variável local de `functionWithNestedLambda`: `localVar`

- Um parâmetro da expressão lambda no qual está aninhado: `level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>Convertendo para um tipo delegado

Uma expressão lambda pode ser convertida implicitamente em um tipo de delegado compatível. Para obter informações sobre os requisitos gerais de compatibilidade, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md). Por exemplo, o exemplo de código a seguir mostra uma expressão lambda que implicitamente converte para `Func(Of Integer, Boolean)` ou uma assinatura delegada correspondente.

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

O exemplo de código a seguir mostra uma expressão lambda que converte implicitamente em `Sub(Of Double, String, Double)` ou uma assinatura delegada correspondente.

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

Ao atribuir expressões lambda a delegados ou passá-las como argumentos para procedimentos, você pode especificar os nomes de parâmetro, mas omitir seus tipos de dados, permitindo que os tipos sejam extraídos do delegado.

## <a name="examples"></a>Exemplos

- O exemplo a seguir define uma expressão lambda que retorna `True` se o argumento anulável tiver um valor atribuído e `False` se seu valor for `Nothing`.

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Tipos de Valor Anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Como criar uma expressão lambda](./how-to-create-a-lambda-expression.md)
- [Conversão de Delegado Reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
