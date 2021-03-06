---
title: Matrizes de parâmetros (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 5a2813b81490e7c2fcf1abcf5fd36ca89d9d7929
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933854"
---
# <a name="parameter-arrays-visual-basic"></a>Matrizes de parâmetros (Visual Basic)
Normalmente, você não pode chamar um procedimento com mais argumentos do que a declaração de procedimento especifica. Quando você precisar de um número indefinido de argumentos, poderá declarar uma *matriz de parâmetros*, que permite que um procedimento aceite uma matriz de valores para um parâmetro. Você não precisa saber o número de elementos na matriz de parâmetros ao definir o procedimento. O tamanho da matriz é determinado individualmente por cada chamada para o procedimento.  
  
## <a name="declaring-a-paramarray"></a>Declarando um ParamArray  
 Você usa a palavra-chave [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) para denotar uma matriz de parâmetros na lista de parâmetros. As seguintes regras se aplicam:  
  
- Um procedimento pode definir apenas uma matriz de parâmetros e deve ser o último parâmetro na definição do procedimento.  
  
- A matriz de parâmetros deve ser passada por valor. É uma boa prática de programação incluir explicitamente a palavra-chave [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) na definição do procedimento.  
  
- A matriz de parâmetros é opcional automaticamente. Seu valor padrão é uma matriz unidimensional vazia do tipo de elemento da matriz de parâmetros.  
  
- Todos os parâmetros anteriores à matriz de parâmetros devem ser necessários. A matriz de parâmetros deve ser o único parâmetro opcional.  
  
## <a name="calling-a-paramarray"></a>Chamando um ParamArray  
 Ao chamar um procedimento que define uma matriz de parâmetros, você pode fornecer o argumento de qualquer uma das seguintes maneiras:  
  
- Nada — ou seja, você pode omitir o argumento [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) . Nesse caso, uma matriz vazia é passada para o procedimento. Você também pode passar a palavra-chave [Nothing](../../../../visual-basic/language-reference/nothing.md) , com o mesmo efeito.  
  
- Uma lista de um número arbitrário de argumentos, separados por vírgulas. O tipo de dados de cada argumento deve ser implicitamente conversível `ParamArray` para o tipo de elemento.  
  
- Uma matriz com o mesmo tipo de elemento que o tipo de elemento da matriz de parâmetros.  
  
 Em todos os casos, o código dentro do procedimento trata a matriz de parâmetros como uma matriz unidimensional com elementos do mesmo tipo de dados `ParamArray` que o tipo de dados.  
  
> [!IMPORTANT]
> Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros, deverá testar o tamanho da matriz que o código de chamada passou para ela. Siga as etapas apropriadas se for muito grande para seu aplicativo. Saiba mais em [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define e chama a `calcSum`função. O `ParamArray` modificador para o `args` parâmetro permite que a função aceite um número variável de argumentos.  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 O exemplo a seguir define um procedimento com uma matriz de parâmetros e gera os valores de todos os elementos de matriz passados para a matriz de parâmetros.  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)
- [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)
