---
title: Indexadores em interfaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 7f52df0283cf057c1cd6cc4fa87c0086da7e61d2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253000"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Indexadores em interfaces (Guia de Programação em C#)
Os indexadores podem ser declarados em uma [interface](../../language-reference/keywords/interface.md). Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../language-reference/keywords/class.md) das seguintes maneiras:  
  
- Os acessadores de interface não usam modificadores.  
  
- Um acessador de interface não tem um corpo.  
  
 Portanto, a finalidade do acessador é indicar se o indexador é leitura/gravação, somente leitura ou somente gravação.  
  
 Este é um exemplo de um acessador de indexador de interface:  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar indexadores de interface.  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface. Por exemplo:  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador. Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária. Ou seja, a seguinte declaração de indexador:  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 implementa o indexador na interface `IEmployee`, enquanto a seguinte declaração:  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 implementa o indexador na interface `ICitizen`.  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Indexadores](./index.md)
- [Propriedades](../classes-and-structs/properties.md)
- [Interfaces](../interfaces/index.md)
