---
title: Comportamento padrão de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 3728d9808eb0ad90d24a894b18857e414906f9f3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045032"
---
# <a name="default-service-behavior"></a>Comportamento padrão de serviço
Este exemplo demonstra como as configurações de comportamento do serviço podem ser definidas. O exemplo se baseia na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato `ICalculator` de serviço. Este exemplo define explicitamente comportamentos de serviço e comportamentos de operação <xref:System.ServiceModel.ServiceBehaviorAttribute> usando <xref:System.ServiceModel.OperationBehaviorAttribute> os atributos e. Você pode configurar comportamentos em arquivos de configuração ou imperativa no código (como demonstra este exemplo).  
  
 Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 A classe de serviço especifica comportamentos com <xref:System.ServiceModel.ServiceBehaviorAttribute> o e <xref:System.ServiceModel.OperationBehaviorAttribute> o, conforme mostrado no exemplo de código a seguir. Todos os valores especificados são os padrões.  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 Os comportamentos de serviço são especificados <xref:System.ServiceModel.ServiceBehaviorAttribute> com o atributo. A tabela a seguir descreve alguns desses comportamentos.  
  
|Comportamento do serviço|Descrição|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|Desliga automaticamente uma sessão na solicitação do cliente.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|Especifica o modo de simultaneidade para cada instância de serviço.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|Especifica o modo de contexto da instância.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|Determina se o contexto de sincronização fornecido deve ser usado, se um for definido. Use isso quando desejar controlar se deseja usar um `WindowsFormsSynchronizationContext` em aplicativos Windows Forms.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|Determina se as exceções de execução sem tratamento geral devem ser convertidas `Fault<string>` em um e enviadas como uma mensagem de falha.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|Especifica o nível de isolamento para transações.|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|Determina se os cabeçalhos de mensagens inesperados causam uma condição de erro.|  
  
 Os comportamentos de operação são especificados usando <xref:System.ServiceModel.OperationBehaviorAttribute> o atributo. A tabela a seguir descreve alguns desses comportamentos.  
  
|Comportamento da operação|Descrição|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|Determina se a conclusão da operação de serviço confirma a transação atual.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|Determina se a operação de serviço se relaciona em uma transação de fluxo do cliente.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|Determina se a operação de serviço representa a identidade do chamador.|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|Determina se as instâncias de serviço são recicladas no início ou no final da chamada de operação de serviço.|  
  
 Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente. O atraso entre as chamadas é o resultado das chamadas `System.Threading.Thread.Sleep()` feitas nas operações de serviço. O restante dos exemplos de comportamento explica esses comportamentos mais detalhadamente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
