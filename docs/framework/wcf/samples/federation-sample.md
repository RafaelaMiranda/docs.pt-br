---
title: Exemplo de federação
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: d3a326f08e78edb79908485361f161c1b6da6625
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044969"
---
# <a name="federation-sample"></a>Exemplo de federação
Este exemplo demonstra a segurança federada.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O Windows Communication Foundation (WCF) oferece suporte para a implantação de arquiteturas de segurança `wsFederationHttpBinding`federada por meio do. O `wsFederationHttpBinding` fornece uma associação segura, confiável e interoperável que envolve o uso de http como o mecanismo de transporte subjacente para a comunicação de solicitação/resposta e text/xml como o formato de conexão para codificação. Para obter mais informações sobre Federação no WCF, consulte [Federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 O cenário é composto de quatro partes:  
  
- Serviço de livraria  
  
- STS da livraria  
  
- STS HomeRealm  
  
- Cliente de livraria  
  
 O serviço de livrarte dá suporte `BrowseBooks` a `BuyBook`duas operações e. Ele permite o `BrowseBooks` acesso anônimo à operação, mas requer acesso autenticado para acessar a `BuyBooks` operação. A autenticação assume a forma de um token emitido pelo STS da livraria. O arquivo de configuração para o serviço de Livrartes aponta os clientes para o `wsFederationHttpBinding`STS da livraria usando o.  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 Em seguida, o STS da livraria requer que os clientes se autentiquem usando um token emitido pelo STS HomeRealm. Novamente, o arquivo de configuração para o STS de Livrarte aponta os clientes para o `wsFederationHttpBinding`STS HomeRealm usando o.  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 A sequência de eventos ao acessar a `BuyBook` operação é a seguinte:  
  
1. O cliente é autenticado no STS HomeRealm usando as credenciais do Windows.  
  
2. O STS HomeRealm emite um token que pode ser usado para autenticar o STS da livraria.  
  
3. O cliente é autenticado no STS da livraria usando o token emitido pelo STS HomeRealm.  
  
4. O STS da livraria emite um token que pode ser usado para autenticar o serviço de livraria.  
  
5. O cliente é autenticado no serviço de livraria usando o token emitido pelo STS da livraria.  
  
6. O cliente acessa a `BuyBook` operação.  
  
 Consulte as instruções a seguir sobre como configurar e executar este exemplo.  
  
> [!NOTE]
> Você deve ter permissões de gravação para o diretório **wwwroot** para executar este exemplo.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Abra a janela de comando do SDK. No caminho de exemplo, execute Setup. bat. Isso cria os diretórios virtuais necessários para o exemplo e instala os certificados necessários com as permissões apropriadas.  
  
    > [!NOTE]
    > O arquivo em lotes setup. bat foi projetado para ser executado em um prompt de comando SDK do Windows. Ele requer que a variável de ambiente MSSDK aponte para o diretório em que o SDK está instalado. Essa variável de ambiente é definida automaticamente em um prompt de comando SDK do Windows. No [!INCLUDE[wv](../../../../includes/wv-md.md)], você deve garantir que a compatibilidade de gerenciamento do IIS 6,0 esteja instalada porque a configuração usa scripts de administrador do IIS. A execução do script de configuração em [!INCLUDE[wv](../../../../includes/wv-md.md)] requer privilégios de administrador.  
  
2. Abra FederationSample. sln no Visual Studio e selecione **Compilar solução** no menu **Compilar** . Isso cria os arquivos de projeto comuns, o serviço de livraria, o STS de livraria, o STS HomeRealm e os implanta no IIS. Isso também cria o aplicativo cliente de livraria e coloca o executável BookStoreClient. exe na pasta FederationSample\BookStoreClient\bin\Debug  
  
3. Clique duas vezes em BookStoreClient. exe. A janela BookStoreClient é exibida.  
  
4. Você pode procurar os manuais disponíveis na livraria clicando em **Procurar livros**.  
  
5. Para comprar um livro específico, selecione o livro na lista e clique em **comprar livro**. O aplicativo inicia e autentica usando a autenticação do Windows com o serviço de token de segurança do HomeRealm.  
  
     O exemplo é configurado para permitir que os usuários adquiram livros que custam $15 ou menos. Tentar comprar livros que custam mais de $15 resultados no cliente que obtém uma mensagem de acesso negado do serviço de armazenamento de livros.  
  
    > [!NOTE]
    > O exemplo não atualiza o limite de crédito do usuário após uma compra. Você pode comprar os livros repetidamente dentro do limite de crédito do usuário (fixo).  
  
#### <a name="to-clean-up"></a>Para limpar  
  
1. Execute Cleanup. bat. Isso exclui os diretórios virtuais que foram criados durante a configuração e também remove os certificados instalados durante a instalação.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
