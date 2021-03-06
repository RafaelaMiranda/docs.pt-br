---
title: Integração de cache ASP.NET
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045784"
---
# <a name="aspnet-caching-integration"></a>Integração de cache ASP.NET

Este exemplo demonstra como utilizar o cache de saída ASP.NET com o modelo de programação WEB HTTP do WCF. Este tópico se concentra no recurso de integração do cache de saída do ASP.NET.

## <a name="demonstrates"></a>Demonstra

Integração com o cache de saída ASP.NET

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Discussão

O exemplo usa o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> para utilizar o cache de saída do ASP.NET com o serviço do Windows Communication Foundation (WCF). O <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> é aplicado às operações de serviço e fornece o nome de um perfil de cache em um arquivo de configuração que deve ser aplicado a respostas da operação especificada.

No arquivo Service.cs do projeto de serviço de exemplo, as `GetCustomer` operações e `GetCustomers` são marcadas com o <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, que fornece o nome do perfil de cache "CacheFor60Seconds". No arquivo Web. config do projeto de serviço, o perfil de cache "CacheFor60Seconds" é fornecido sob o elemento`caching`< > de <`system.web`>. Para esse perfil de cache, o valor do `duration` atributo é "60", portanto, as respostas associadas a esse perfil são armazenadas em cache no cache de saída ASP.net por 60 segundos. Além disso, para esse perfil de cache `varmByParam` , o atributo é definido como "Format" para que as solicitações com `format` valores diferentes para o parâmetro de cadeia de caracteres de consulta tenham suas respostas armazenadas em cache separadamente. Por fim, o atributo do `varyByHeader` perfil de cache é definido como "Accept", portanto, as solicitações com valores de cabeçalho Accept diferentes têm suas respostas armazenadas em cache separadamente.

Program.cs no projeto do cliente demonstra como um cliente desse tipo pode ser criado usando <xref:System.Net.HttpWebRequest>o. Observe que essa é apenas uma maneira de acessar um serviço WCF. Também é possível acessar o serviço usando outras classes de .NET Framework, como a fábrica de canais do <xref:System.Net.WebClient>WCF e o. Outros exemplos no SDK (como o exemplo de [serviço http básico](../../../../docs/framework/wcf/samples/basic-http-service.md) ) ilustram como usar essas classes para se comunicar com um serviço WCF.

## <a name="to-run-the-sample"></a>Para executar a amostra

O exemplo consiste em três projetos:

- **Serviço**: Um projeto de aplicativo Web que inclui um serviço HTTP do WCF hospedado em ASP.NET.

- **Cliente**: Um projeto de aplicativo de console que faz chamadas para o serviço.

- **Comum**: Uma biblioteca compartilhada que contém o tipo de cliente usado pelo cliente e serviço.

À medida que o aplicativo de console do cliente é executado, o cliente faz solicitações ao serviço e grava as informações pertinentes das respostas na janela do console.

#### <a name="to-run-the-sample"></a>Para executar a amostra

1. Abra a solução para o exemplo de integração do cache ASP.NET.

2. Pressione CTRL+SHIFT+B para criar a solução.

3. Se a janela de **Gerenciador de soluções** ainda não estiver aberta, pressione CTRL + W + S.

4. Na janela **Gerenciador de soluções** , clique com o botão direito do mouse no projeto de **serviço** e selecione **Iniciar nova instância**. Isso inicia o servidor de desenvolvimento do ASP.NET, que hospeda o serviço.

5. Na janela **Gerenciador de soluções** , clique com o botão direito do mouse no projeto **cliente** e selecione **Iniciar nova instância**.

6. A janela do console do cliente é exibida e fornece o URI do serviço em execução e o URI da página de ajuda HTML para o serviço em execução. Em qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de ajuda em um navegador.

7. À medida que o exemplo é executado, o cliente grava o status da atividade atual.

8. Pressione qualquer tecla para encerrar o aplicativo de console do cliente.

9. Pressione SHIFT + F5 para parar a depuração do serviço.

10. Na área de notificação do Windows, clique com o botão direito do mouse no ícone do servidor de desenvolvimento ASP.NET e selecione **parar**.
