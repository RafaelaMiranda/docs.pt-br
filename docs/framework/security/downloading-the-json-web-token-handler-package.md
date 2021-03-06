---
title: Baixando o Pacote do Manipulador de Token da Web JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: a8685a71d46778d932595965f32c0041b176bd83
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633522"
---
# <a name="download-the-json-web-token-handler-package"></a>Baixe o pacote do manipulador de Token Web JSON

Este tópico descreve como baixar e usar o Manipulador de Token Web JSON no projeto.

A extensão Manipulador de Token Web JSON está disponível como um pacote NuGet, que adiciona os assemblies e as referências necessárias ao projeto. Se você ainda não tiver o NuGet instalado, acesse [nuget.org](https://nuget.org) para instalá-lo. Você pode ver o histórico de controle de versão para a extensão visitando sua página no NuGet: [Manipulador de Token Web JSON no NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)

## <a name="use-the-package-manager-gui"></a>Usar a GUI do Gerenciador de pacotes

1. No Visual Studio, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções** e, em seguida, selecione **Gerenciar Pacotes NuGet**.

2. Na janela **Gerenciar Pacotes NuGet**, clique na caixa de pesquisa, insira `JWT Token Handler` e pressione **Enter**.

3. No painel de resultados, clique no botão **Instalar** do primeiro resultado.

4. O download do pacote será iniciado. Antes que ele seja adicionado ao projeto, a caixa de diálogo Aceitação da Licença será exibida. Se concordar com os termos de licença, clique em **Eu Aceito**.

5. Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.

## <a name="use-the-package-manager-console"></a>Use o Console do Gerenciador de pacotes

1. No Visual Studio, clique em **ferramentas** > **Gerenciador de pacotes NuGet** > **Package Manager Console**.

2. O **Console do Gerenciador de Pacotes** será exibido. Insira o seguinte texto e pressione **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. Os últimos assemblies do Manipulador de Token Web JSON serão baixados e adicionados ao projeto.
