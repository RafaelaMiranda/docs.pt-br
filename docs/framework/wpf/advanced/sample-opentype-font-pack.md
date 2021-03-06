---
title: Pacote de fontes OpenType de amostra
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 76438b85a12d75efa0fc106a645fb592b3205fad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960977"
---
# <a name="sample-opentype-font-pack"></a>Pacote de fontes OpenType de amostra
Este tópico fornece uma visão geral das fontes OpenType de exemplo que são distribuídas [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]com o. As fontes de exemplo dão suporte a recursos OpenType estendidos que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] podem ser usados por aplicativos.  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Fontes no pacote de fontes OpenType  
 O [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] fornece um conjunto de fontes OpenType de exemplo que você pode usar na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] criação de aplicativos. As fontes de exemplo são fornecidas sob licença da Ascender Corporation. Essas fontes implementam apenas um subconjunto do total de recursos definidos pelo formato OpenType. A tabela a seguir lista os nomes das fontes OpenType de exemplo.  
  
|**Nome**|**Arquivo**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 A ilustração a seguir mostra a aparência das fontes OpenType de exemplo.  
  
 ![Lista de nomes de fontes no pacote de fontes de exemplo](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 As fontes de exemplo são fornecidas sob licença da Ascender Corporation. Ascender é um provedor de produtos avançados de fontes. Para licenciar versões estendidas ou personalizadas das fontes de exemplo, consulte [Site de Web da Ascender Corporation](https://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
> Como desenvolvedor, é sua responsabilidade verificar se você tem os direitos de licença necessários de qualquer fonte inserida em um aplicativo ou redistribuída de outra forma.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalando as fontes  
 Você tem a opção de instalar as fontes OpenType de exemplo no diretório padrão de fontes do Windows, **\WINDOWS\Fonts**. Use o painel de controle Fontes para instalar as fontes. Depois que essas fontes estiverem em seu computador, elas poderão ser acessadas por todos os aplicativos que fazem referência às fontes padrão do Windows. Você pode exibir um conjunto representativo de caracteres em vários tamanhos de fonte clicando duas vezes no arquivo de fonte. A captura de tela a seguir mostra o arquivo de fonte Lindsey, Linds.tff.  
  
 ![Fonte &#40;Lindsey OpenType&#41; ](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Exibindo a fonte Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Usando as fontes  
 Há duas maneiras de usar fontes no seu aplicativo. Você pode adicionar fontes ao seu aplicativo como itens de conteúdo de projeto que não são inseridos como recursos em um assembly. Como alternativa, você pode adicionar fontes ao seu aplicativo como itens de recurso de projeto que são inseridos nos arquivos de assembly do aplicativo. Para obter mais informações, consulte [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Documents.Typography>
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md)
