---
title: 'Como: Determinar a versão instalada do WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: ffbd9a4c7f66dff9c8773dff4259551e20aa963d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052450"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>Como: Determinar a versão instalada do WPF
O número de versão para a versão instalada atual do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] está localizado em de **registro**.  
  
 Para localizar o número de versão:  
  
1. No menu **Iniciar** , clique em **Executar**.  
  
2. Na **aberto**, digite **regedit.exe**.  
  
3. Abra a seguinte chave:  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] número de versão é armazenado na **versão** valor.
