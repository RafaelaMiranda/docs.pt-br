---
title: Delegados genéricos para manipulação de matrizes e listas
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f37f55f5af70a232952bdb94f0c111a27fcbab1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948780"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegados genéricos para manipulação de matrizes e listas
Este tópico fornece uma visão geral de delegados genéricos para conversões, predicados de pesquisa e ações a serem tomadas nos elementos de uma matriz ou coleção.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegados genéricos para manipulação de matrizes e listas  
 O delegado <xref:System.Action%601> genérico representa um método que executa uma ação em um elemento do tipo especificado. Você pode criar um método que executa a ação desejada no elemento, criar uma instância do delegado <xref:System.Action%601> para representar esse método e, em seguida, passar a matriz e o delegado para o método <xref:System.Array.ForEach%2A?displayProperty=nameWithType> genérico estático. O método é chamado para cada elemento da matriz.  
  
 A classe genérica <xref:System.Collections.Generic.List%601> também fornece um método <xref:System.Collections.Generic.List%601.ForEach%2A> que usa o delegado <xref:System.Action%601>. Este método não é genérico.  
  
> [!NOTE]
> Isso é um argumento interessante sobre tipos e métodos genéricos. O método <xref:System.Array.ForEach%2A?displayProperty=nameWithType> deve ser estático (`Shared` no Visual Basic) e genérico porque <xref:System.Array> não é um tipo genérico; o único motivo pelo qual você pode especificar um tipo em que o <xref:System.Array.ForEach%2A?displayProperty=nameWithType> deve operar é que o método tenha sua própria lista de parâmetros de tipo. Por outro lado, o método <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> não genérico pertence à classe genérica <xref:System.Collections.Generic.List%601>; portanto, ele simplesmente usa o parâmetro de tipo de sua classe. A classe é fortemente tipada; portanto, o método pode ser um método de instância.  
  
 O delegado <xref:System.Predicate%601> genérico representa um método que determina se um determinado elemento atende aos critérios que você definir. Você pode usá-lo com os seguintes métodos genéricos estáticos de <xref:System.Array> para procurar um elemento ou um conjunto de elementos: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A> e <xref:System.Array.TrueForAll%2A>.  
  
 O <xref:System.Predicate%601> também funciona com os métodos de instância não genérica correspondentes da classe genérica <xref:System.Collections.Generic.List%601>.  
  
 O delegado <xref:System.Comparison%601> genérico permite que você forneça uma ordem de classificação para elementos de matriz ou lista que não têm uma ordem de classificação nativa, ou para substituir a ordem de classificação nativa. Crie um método que executa a comparação, crie uma instância do delegado <xref:System.Comparison%601> para representar o método e, em seguida, passe a matriz e o delegado para o método <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> genérico estático. A classe <xref:System.Collections.Generic.List%601> genérica fornece uma sobrecarga do método de instância correspondente, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 O delegado <xref:System.Converter%602> genérico permite que você defina uma conversão entre dois tipos e para converter uma matriz de um tipo em uma matriz do outro ou para converter uma lista de um tipo em uma lista do outro. Crie um método que converte os elementos de uma lista existente para um novo tipo, crie uma instância delegada para representar o método e usar o método <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> estático genérico para produzir uma matriz do novo tipo da matriz original, ou o método de instância <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> genérico para produzir uma lista do novo tipo da lista original.  
  
### <a name="chaining-delegates"></a>Encadeando delegados  
 Muitos dos métodos que usam esses delegados retornam uma matriz ou lista, que pode ser passada para outro método. Por exemplo, se você quiser selecionar determinados elementos de uma matriz, converta esses elementos em um novo tipo e salve-os em uma nova matriz, você pode passar a matriz retornada pelo método <xref:System.Array.FindAll%2A> genérico para o método <xref:System.Array.ConvertAll%2A> genérico. Se o novo tipo de elemento não tiver uma ordem de classificação natural, você poderá passar a matriz retornada pelo método <xref:System.Array.ConvertAll%2A> genérico para o método <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> genérico.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genéricos](../../../docs/standard/generics/index.md)
- [Coleções genéricas no .NET Framework](../../../docs/standard/generics/collections.md)
- [Interfaces genéricas](../../../docs/standard/generics/interfaces.md)
- [Covariância e Contravariância](../../../docs/standard/generics/covariance-and-contravariance.md)
