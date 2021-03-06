---
title: Valores de variável de objeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 728f097b3c084e5292cb2d2bf5a0c1d20bdad922
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004591"
---
# <a name="object-variable-values-visual-basic"></a>Valores de variável de objeto (Visual Basic)
Uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) pode se referir a dados de qualquer tipo. O valor que você armazena em uma variável `Object` é mantido em outro lugar na memória, enquanto a própria variável contém um ponteiro para os dados.  
  
## <a name="object-classifier-functions"></a>Funções de classificação de objeto  
 Visual Basic fornece funções que retornam informações sobre o que uma variável `Object` refere, conforme mostrado na tabela a seguir.  
  
|Função|Retornará true se a variável de objeto se referir a|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Uma matriz de valores, em vez de um único valor|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Um valor de [tipo de dados Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) ou uma cadeia de caracteres que pode ser interpretada como um valor de data e hora|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Um objeto do tipo <xref:System.DBNull>, que representa dados ausentes ou inexistentes|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Um objeto de exceção, que deriva de <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nada](../../../../visual-basic/language-reference/nothing.md), ou seja, nenhum objeto está atribuído atualmente à variável|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Um número ou uma cadeia de caracteres que pode ser interpretada como um número|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Um tipo de referência (como uma cadeia de caracteres, matriz, delegado ou tipo de classe)|  
  
 Você pode usar essas funções para evitar o envio de um valor inválido para uma operação ou um procedimento.  
  
## <a name="typeof-operator"></a>Operador TypeOf  
 Você também pode usar o [operador typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) para determinar se uma variável de objeto atualmente se refere a um tipo de dados específico. A expressão `TypeOf`... `Is` é avaliada como `True` se o tipo de tempo de execução do operando é derivado de ou implementa o tipo especificado.  
  
 O exemplo a seguir usa `TypeOf` em variáveis de objeto referindo-se a tipos de referência e valor.  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 O exemplo anterior grava as seguintes linhas na janela de **depuração** :  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 A variável de objeto `num` refere-se a dados do tipo `Integer` e `frm` refere-se a um objeto da classe <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Matrizes de objetos  
 Você pode declarar e usar uma matriz de variáveis `Object`. Isso é útil quando você precisa lidar com uma variedade de tipos de dados e classes de objeto. Todos os elementos em uma matriz devem ter o mesmo tipo de dados declarado. Declarar esse tipo de dados como `Object` permite que você armazene objetos e instâncias de classe junto com outros tipos de dados na matriz.  
  
## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Como: Consulte a instância atual de um objeto @ no__t-0
- [Como: Determine que tipo uma variável de objeto se refere a @ no__t-0
- [Como: Determinar se dois objetos estão relacionados a @ no__t-0
- [Como: Determinar se dois objetos são idênticos a @ no__t-0
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
