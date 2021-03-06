---
title: Visão geral do controle TrackBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 1606db73485944f3dfa8b9c084bffda817520c7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009260"
---
# <a name="trackbar-control-overview-windows-forms"></a>Visão geral do controle TrackBar (Windows Forms)
Os formulários do Windows <xref:System.Windows.Forms.TrackBar> controle (também chamado de um controle de "controle deslizante") é usado para navegar por uma grande quantidade de informações ou para ajustar visualmente um ajuste numérico. O <xref:System.Windows.Forms.TrackBar> controle tem duas partes: o elevador, também conhecido como um controle deslizante e as marcas de escala. O elevador é parte que pode ser ajustada. Sua posição corresponde à <xref:System.Windows.Forms.TrackBar.Value%2A> propriedade. As marcas de escala são indicadores visuais espaçados em intervalos regulares. A trackbar se move em incrementos especificados e pode ser alinhada horizontalmente ou verticalmente. Por exemplo, é possível usar a trackbar para controlar a taxa de intermitência do cursor ou a velocidade do mouse em um sistema.  
  
## <a name="key-properties"></a>Propriedades da chave  
 As propriedades da chave de <xref:System.Windows.Forms.TrackBar> controle estão <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A>, e <xref:System.Windows.Forms.TrackBar.Maximum%2A>. <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> é o espaçamento entre os tiques. <xref:System.Windows.Forms.TrackBar.Minimum%2A> e <xref:System.Windows.Forms.TrackBar.Maximum%2A> são menores e maiores valores que podem ser representados na track bar.  
  
 Outras duas propriedades importantes são <xref:System.Windows.Forms.TrackBar.SmallChange%2A> e <xref:System.Windows.Forms.TrackBar.LargeChange%2A>. O valor da <xref:System.Windows.Forms.TrackBar.SmallChange%2A> propriedade é o número de posições que o elevador move em resposta a ter a tecla de seta esquerda ou direita pressionada. O valor da <xref:System.Windows.Forms.TrackBar.LargeChange%2A> propriedade é o número de posições que o elevador move em resposta a ter a tecla PAGE UP ou PAGE DOWN pressionada, ou em resposta a mouse clica na track bar em ambos os lados do elevador.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.TrackBar>
- [Controle TrackBar](trackbar-control-windows-forms.md)
