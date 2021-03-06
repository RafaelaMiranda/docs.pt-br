---
title: 'Como: Organizar lado a lado uma forma com uma imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: a906db44a548361df2822efa24d1dd1849cb5a24
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063731"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Como: Organizar lado a lado uma forma com uma imagem
Da mesma forma que blocos podem ser colocados lado a lado para recobrir um piso, imagens retangulares podem ser colocadas umas ao lado das outras para preencher (organizar lado a lado) uma forma. Para organizar o interior de uma forma lado a lado, use um pincel de textura. Quando você constrói uma <xref:System.Drawing.TextureBrush> do objeto, um dos argumentos passados para o construtor é um <xref:System.Drawing.Image> objeto. Quando você usa o pincel de textura para pintar o interior de uma forma, ela será preenchida com repetidas cópias dessa imagem.  
  
 A propriedade de modo de encapsulamento do <xref:System.Drawing.TextureBrush> objeto determina como a imagem é orientada conforme ele é repetida em uma grade retangular. Você pode fazer todos os blocos na grade terem a mesma orientação ou fazer com que a imagem fique invertida de uma posição de grade para a próxima. A inversão pode ser horizontal, vertical ou ambas. Os exemplos a seguir demonstram organização lado a lado com tipos diferentes de inversão.  
  
### <a name="to-tile-an-image"></a>Organizar uma imagem lado a lado  
  
- Este exemplo usa a imagem de 75 × 75 a seguir para organização lado a lado em um retângulo de 200 × 200.  
  
 ![A imagem de bloco que mostra uma casa vermelha e uma árvore.](./media/how-to-tile-a-shape-with-an-image/rectangle-tile-200x200.gif)  
  
- A ilustração a seguir mostra como o retângulo é organizado lado a lado com a imagem. Observe que todos os blocos têm a mesma orientação; não há nenhum inversão.  
  
 ![Um retângulo lado a lado com a imagem usando a mesma orientação para todos os blocos.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-no-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>Inverter uma imagem horizontalmente com organização lado a lado  
  
- Este exemplo usa a mesma imagem de 75 × 75 para preencher um retângulo 200 × 200. O modo de encapsulamento é definido para inverter a imagem horizontalmente. A ilustração a seguir mostra como o retângulo é organizado lado a lado com a imagem. Observe que, ao mudar de um bloco para o próximo em uma determinada linha, a imagem é invertida horizontalmente.  
  
 ![Um retângulo lado a lado com a imagem é invertida horizontalmente.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>Inverter uma imagem verticalmente com organização lado a lado  
  
- Este exemplo usa a mesma imagem de 75 × 75 para preencher um retângulo 200 × 200. O modo de encapsulamento é definido para inverter a imagem verticalmente.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>Inverter uma imagem horizontalmente e verticalmente com organização lado a lado  
  
- Este exemplo usa a mesma imagem de 75 × 75 para organizar lado a lado um retângulo de 200 × 200. O modo de encapsulamento é definido para inverter a imagem tanto horizontalmente quanto verticalmente. A ilustração a seguir mostra como o retângulo é organizado lado a lado pela imagem. Observe que, ao mudar de um bloco para o próximo em uma determinada linha, a imagem é invertida horizontalmente e, ao mudar de um bloco para o próximo em uma determinada coluna, a imagem é invertida verticalmente.  
  
 ![Um retângulo lado a lado com a imagem invertida horizontalmente e verticalmente.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-vertical-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Consulte também

- [Usando um pincel para preencher formas](using-a-brush-to-fill-shapes.md)
