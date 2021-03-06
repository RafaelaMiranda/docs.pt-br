---
title: Vários contratos
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 257b3f7946a7185cdb82bda88e64e543afa85707
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039199"
---
# <a name="multiple-contracts"></a>Vários contratos
O exemplo de vários contratos demonstra como implementar mais de um contrato em um serviço e como configurar pontos de extremidade para se comunicar com cada um dos contratos implementados. Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço foi modificado para definir dois contratos, o `ICalculator` contrato e o `ICalculatorSession` contrato.  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 A classe de serviço implementa os `ICalculator` contratos `ICalculatorSession` e. Como um dos contratos requer uma sessão, o serviço usa o <xref:System.ServiceModel.InstanceContextMode.PerSession> modo de instância para manter o estado durante o tempo de vida da sessão.  
  
 A configuração de serviço foi modificada para definir dois pontos de extremidade para expor cada contrato. O `ICalculator` ponto de extremidade é exposto no endereço base usando `basicHttpBinding`um. O `ICalculatorSession` ponto de extremidade é exposto no BaseAddress/Session usando `wsHttpBinding` um `BindingWithSession`com `bindingConfiguration` o atributo definido como, conforme mostrado na seguinte configuração de exemplo.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 O código do cliente gerado agora inclui uma classe de cliente para o `ICalculator` contrato original e para `ICalculatorSession` o novo contrato. A configuração do cliente e o código foram modificados para se comunicar com cada contrato no ponto de extremidade de serviço apropriado.  
  
 O cliente é um aplicativo do Windows do console (. exe). O serviço é hospedado pelo Serviços de Informações da Internet (IIS).  
  
 A janela do console do cliente exibe as operações enviadas para cada um dos pontos de extremidade, primeiro o ponto final básico, seguido pelo ponto de extremidade seguro.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
