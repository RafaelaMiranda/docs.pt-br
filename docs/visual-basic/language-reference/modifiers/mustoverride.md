---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: f5932b28c4664dd59dad829228f2186e78108af5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661251"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Especifica que uma propriedade ou procedimento não está implementado nesta classe e deve ser substituído em uma classe derivada antes que ele pode ser usado.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `MustOverride` somente em uma instrução de declaração de propriedade ou procedimento. A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe, e a classe deve ser marcada [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Regras  
  
- **Declaração incompleta.** Quando você especifica `MustOverride`, você não fornecer quaisquer linhas adicionais de código para a propriedade ou procedimento, não até mesmo os `End Function`, `End Property`, ou `End Sub` instrução.  
  
- **Modificadores combinados.** Não é possível especificar `MustOverride` junto com `NotOverridable`, `Overridable`, ou `Shared` na mesma declaração.  
  
- **Sombreamento e sobreposição.** Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Termos alternativos.** Um elemento que não pode ser usado, exceto em uma substituição às vezes é chamado um *pura virtual* elemento.  
  
 O `MustOverride` modificador pode ser usado nestes contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
