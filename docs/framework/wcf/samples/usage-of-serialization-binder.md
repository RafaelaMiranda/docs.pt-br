---
title: Utilização do associador de serialização
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 10900950b935b484053fe8e37263f0dfc25eba99
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348450"
---
# <a name="usage-of-serialization-binder"></a>Utilização do associador de serialização
Este exemplo mostra como usar o <xref:System.Runtime.Serialization.SerializationBinder> para alterar a versão de um tipo genérico quando ele é serializado.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como duas entidades que são direcionamento de versões diferentes podem do .NET Framework se comunicar usando o formatador binário e o associador de serialização.  
  
Esse exemplo foi desenvolvido usando a comunicação remota do .NET. Ele consiste em um servidor de direcionamento [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], que implementa um contrato com tipos genéricos e dois clientes diferentes, um direcionamento .NET Framework 2.0 e o direcionamento de outro [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 As conexões de servidor um <xref:System.Runtime.Serialization.SerializationBinder> ao formatador binário para poder alterar a versão dos tipos de acordo sobre serialização, portanto, ambos os clientes podem desserializar esses tipos corretamente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1. Para executar o cliente, clique com botão direito a solução, SBGenericsVTS (6 projetos) e, em seguida, selecione **propriedades**.  
  
2. Na **propriedades comuns**, selecione **projeto de inicialização**, em seguida, selecione **vários projetos de inicialização**.  
  
3. Selecione **Server** , em seguida, primeiro **Client20** e, em seguida, **Client40**. Selecione o **inicie** ação para esses três projetos e deixe o restante definido como **None**.  
  
4. Clique em **Okey** e, em seguida, pressione F5 para executar o exemplo.
