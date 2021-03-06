---
title: Procedimento principal no Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 1c76e3ade0b383727c3241fdaf5ae44b677559c8
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775690"
---
# <a name="main-procedure-in-visual-basic"></a>Procedimento principal no Visual Basic
Cada aplicativo de Visual Basic deve conter um procedimento chamado `Main`. Esse procedimento serve como o ponto de partida e o controle geral para seu aplicativo. O .NET Framework chama o procedimento `Main` quando ele carregou o aplicativo e está pronto para passar o controle para ele. A menos que você esteja criando um aplicativo de Windows Forms, você deve escrever o procedimento de `Main` para aplicativos que são executados por conta própria.

 `Main` contém o código que é executado primeiro. No `Main`, você pode determinar qual formulário deve ser carregado primeiro quando o programa for iniciado, descobrir se uma cópia do seu aplicativo já está em execução no sistema, estabelecer um conjunto de variáveis para seu aplicativo ou abrir um banco de dados que o aplicativo requer.

## <a name="requirements-for-the-main-procedure"></a>Requisitos para o procedimento principal
 Um arquivo que é executado por conta própria (normalmente com extensão. exe) deve conter um procedimento `Main`. Uma biblioteca (por exemplo, com extensão. dll) não é executada por conta própria e não requer um procedimento de `Main`. Os requisitos para os diferentes tipos de projetos que você pode criar são os seguintes:

- Os aplicativos de console são executados por conta própria e você deve fornecer pelo menos um procedimento de `Main`.

- Windows Forms aplicativos são executados por conta própria. No entanto, o compilador de Visual Basic gera automaticamente um procedimento de `Main` nesse aplicativo, e você não precisa escrever um.

- As bibliotecas de classes não exigem um procedimento `Main`. Isso inclui bibliotecas de controle do Windows e bibliotecas de controle da Web. Os aplicativos Web são implantados como bibliotecas de classes.

## <a name="declaring-the-main-procedure"></a>Declarando o procedimento principal
 Há quatro maneiras de declarar o procedimento de `Main`. Ele pode usar argumentos ou não, e pode retornar um valor ou não.

> [!NOTE]
> Se você declarar `Main` em uma classe, deverá usar a palavra-chave `Shared`. Em um módulo, `Main` não precisa ser `Shared`.

- A maneira mais simples é declarar um procedimento de `Sub` que não use argumentos nem retorne um valor.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main` também pode retornar um valor de `Integer`, que o sistema operacional usa como o código de saída para seu programa. Outros programas podem testar esse código examinando o valor ERRORLEVEL do Windows. Para retornar um código de saída, você deve declarar `Main` como um procedimento `Function` em vez de um procedimento `Sub`.

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- `Main` também pode pegar uma matriz `String` como um argumento. Cada cadeia de caracteres na matriz contém um dos argumentos de linha de comando usados para invocar seu programa. Você pode executar ações diferentes dependendo de seus valores.

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- Você pode declarar `Main` para examinar os argumentos de linha de comando, mas não retornar um código de saída, da seguinte maneira.

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Estrutura de um programa de Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)
