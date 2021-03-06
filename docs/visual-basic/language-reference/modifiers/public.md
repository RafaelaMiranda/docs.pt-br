---
title: Público (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0b8c31facc3605ff5a77aecf7b11456b33fbab72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647741"
---
# <a name="public-visual-basic"></a>Público (Visual Basic)
Especifica que um ou mais elementos de programação declarados não têm nenhuma restrição de acesso.  
  
## <a name="remarks"></a>Comentários  
 Se você estiver publicando um componente ou um conjunto de componentes, como uma biblioteca de classes, geralmente você deseja que os elementos de programação para ser acessado por qualquer código que interopera com o assembly. Para concede tal acesso ilimitado em um elemento, você pode declará-la com `Public`.  
  
 Acesso público é o nível normal para um elemento de programação quando você não precisa limitar o acesso a ele. Observe que o nível de acesso de um elemento declarado dentro de uma interface, módulo, classe ou estrutura padrão é `Public` se você não declarar o contrário.  
  
## <a name="rules"></a>Regras  
  
- **Contexto da declaração.** Você pode usar `Public` apenas no nível de namespace ou módulo. Isso significa que o contexto da declaração para um `Public` elemento deve ser um arquivo de origem, namespace, interface, módulo, classe ou estrutura e não pode ser um procedimento.  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Todo o código que pode acessar um módulo, classe ou estrutura pode acessar seu `Public` elementos.  
  
- **Acesso padrão.** Variáveis locais dentro de um procedimento usam como padrão acesso público e você não podem usar qualquer modificador de acesso sobre eles.  
  
- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para obter uma comparação os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Public` modificador pode ser usado nestes contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Particular Protegido](private-protected.md)
- [Amigo Protegido](protected-friend.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
