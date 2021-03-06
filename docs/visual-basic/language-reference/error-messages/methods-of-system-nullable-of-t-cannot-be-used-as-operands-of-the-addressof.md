---
title: Os métodos de 'System.Nullable(Of T)' não podem ser usados como operandos do operador 'AddressOf'
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: e55e561fa20a3740d352537958681b0a66fc381e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592039"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>Os métodos de 'System.Nullable(Of T)' não podem ser usados como operandos do operador 'AddressOf'
Uma instrução usa o `AddressOf` operador com um operando que representa um procedimento do <xref:System.Nullable%601> estrutura.  
  
 **ID do erro:** BC32126  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Substitua o nome do procedimento na `AddressOf` cláusula com um operando que não é um membro de <xref:System.Nullable%601>.  
  
- Escrever uma classe que encapsula o método de <xref:System.Nullable%601> que você deseja usar. No exemplo a seguir, o `NullableWrapper` classe define um novo método chamado `GetValueOrDefault`. Como esse novo método não é um membro da <xref:System.Nullable%601>, ele pode ser aplicado a `nullInstance`, uma instância de um tipo anulável, para formar um argumento para `AddressOf`.  
  
```vb  
Module Module1  
  
    Delegate Function Deleg() As Integer  
  
    Sub Main()  
        Dim nullInstance As New Nullable(Of Integer)(1)  
  
        Dim del As Deleg  
  
        ' GetValueOrDefault is a method of the Nullable generic  
        ' type. It cannot be used as an operand of AddressOf.  
        ' del = AddressOf nullInstance.GetValueOrDefault  
  
        ' The following line uses the GetValueOrDefault method  
        ' defined in the NullableWrapper class.  
        del = AddressOf (New NullableWrapper(  
            Of Integer)(nullInstance)).GetValueOrDefault  
  
        Console.WriteLine(del.Invoke())  
    End Sub  
  
    Class NullableWrapper(Of T As Structure)  
        Private m_Value As Nullable(Of T)  
  
        Sub New(ByVal Value As Nullable(Of T))  
            m_Value = Value  
        End Sub  
  
        Public Function GetValueOrDefault() As T  
            Return m_Value.Value  
        End Function  
    End Class  
End Module  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Nullable%601>
- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
