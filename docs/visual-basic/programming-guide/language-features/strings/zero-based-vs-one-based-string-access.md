---
title: Acesso a cadeias de caracteres baseado em Acesso com base em uma cadeia de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591755"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>Acesso a cadeias de caracteres baseado em Acesso com base em uma cadeia de caracteres no Visual Basic
Este tópico compara como Visual Basic e o .NET Framework fornecem acesso aos caracteres em uma cadeia de caracteres. O .NET Framework sempre fornece acesso baseado em zero para os caracteres em uma cadeia de caracteres, enquanto o Visual Basic fornece acesso baseado em zero e um, dependendo da função.  
  
## <a name="one-based"></a>Baseado em um  
 Para obter um exemplo de uma função do Visual Basic baseado em um, considere o `Mid` função. Ele usa um argumento que indica a posição do caractere no qual será iniciada a subcadeia de caracteres, começando pela posição 1. O .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> método utiliza um índice do caractere na cadeia de caracteres no qual a subcadeia de caracteres deve começar, começando pela posição 0. Portanto, se você tiver uma cadeia de caracteres "ABCDE", os caracteres individuais são numerados 1,2,3,4,5 para uso com o `Mid` função, mas 0,1,2,3,4 para uso com o <xref:System.String.Substring%2A?displayProperty=nameWithType> método.  
  
## <a name="zero-based"></a>Com base em zero  
 Para obter um exemplo de uma função do Visual Basic com base em zero, considere o `Split` função. Ele divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres. O .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> método também divide uma cadeia de caracteres e retorna uma matriz que contém as subcadeias de caracteres. Porque o `Split` função e <xref:System.String.Split%2A> método retornam matrizes do .NET Framework, eles devem ser baseado em zero.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
