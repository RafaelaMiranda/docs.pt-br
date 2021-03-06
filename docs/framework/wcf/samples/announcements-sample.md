---
title: Exemplo de anúncios
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 1acf51ebe36872424be1e0fdda65a7d18aa737f2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045792"
---
# <a name="announcements-sample"></a>Exemplo de anúncios

Este exemplo mostra como usar a funcionalidade de anúncio do recurso de descoberta. Os anúncios permitem que os serviços enviem mensagens de comunicado que contêm metadados sobre o serviço. Por padrão, um comunicado de saudação é enviado quando o serviço é iniciado e um comunicado de adeus é enviado quando o serviço é desligado. Esses comunicados podem ser multicast ou podem ser enviados ponto a ponto. Este exemplo consiste em dois projetos serviço e cliente.

## <a name="service"></a>Serviço

Este projeto contém um serviço de calculadora auto-hospedado. `Main` No método, um host de serviço é criado e um ponto de extremidade de serviço é adicionado a ele. Em seguida, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> um é criado. Para habilitar anúncios, um ponto de extremidade de anúncio deve ser adicionado <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>ao. Nesse caso, um ponto de extremidade padrão, usando o multicast UDP, é adicionado como o ponto de extremidade do anúncio. Isso transmite os anúncios por um endereço UDP conhecido.

```csharp
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);

     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();

     // Announce the availability of the service over UDP multicast
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());

    // Make the service discoverable over UDP multicast.
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());
    serviceHost.Open();
    // ...
}
```

## <a name="client"></a>Cliente

Neste projeto, observe que o cliente hospeda um <xref:System.ServiceModel.Discovery.AnnouncementService>. Além disso, dois delegados são registrados com eventos. Esses eventos ditam o que o cliente faz quando anúncios online e offline são recebidos.

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

Os `OnOnlineEvent` métodos `OnOfflineEvent` e lidam com as mensagens de anúncio de saudação e adeus, respectivamente.

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine();
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);
}
```

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Este exemplo usa pontos de extremidade HTTP e para executar esse exemplo, as ACLs de URL adequadas devem ser adicionadas consulte Configurando [http e HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes. A execução do comando a seguir em um privilégio elevado deve adicionar as ACLs apropriadas. Talvez você queira substituir seu domínio e nome de usuário pelos argumentos a seguir se o comando não funcionar como está. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Compile a solução.

3. Execute o aplicativo Client. exe.

4. Execute o aplicativo Service. exe. Observação o cliente recebe um comunicado online.

5. Feche o aplicativo Service. exe. Observação o cliente recebe um anúncio offline.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
