---
title: Interfaces de hospedagem CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80404e65263aa4ad245a8c8213630a4736bd7b11
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456880"
---
# <a name="clr-hosting-interfaces"></a>Interfaces de hospedagem CLR
Esta seção descreve as interfaces não gerenciadas hosts podem usar para integrar o common language runtime (CLR) em seus aplicativos. As informações referem-se para a versão do .NET Framework 2.0 e versões posteriores. Essas interfaces habilite o host controlar muitos outros aspectos do tempo de execução que era possível nas versões 1.0 e 1.1 e fornecem muito mais integração entre o CLR e o modelo de execução do host.  
  
 No .NET Framework versão 1.0 e 1.1, o modelo de hospedagem habilitado um host não gerenciado carregar o CLR em um processo, a definir certas configurações e para receber notificações de eventos. No entanto, em geral, o host e o CLR foi executada independentemente em que o processo. No .NET Framework versão 2.0 e versões posteriores, novas camadas de abstração permitem que o host fornece muitos dos recursos fornecidos atualmente pelos tipos no assembly do Win32 e estender o conjunto de recursos que o host pode configurar.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Fornece um método que executa um retorno de chamada para um evento registrado.  
  
 [Interface IApartmentCallback](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Fornece métodos para fazer retornos de chamada dentro de um apartamento.  
  
 [Interface IAppDomainBinding](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Fornece métodos para a definição de configuração de tempo de execução.  
  
 [Interface ICatalogServices](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Fornece métodos para serviços de catalogação. (Esta interface dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.)  
  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Fornece métodos que oferecem suporte à comunicação entre o host e o CLR sobre assemblies.  
  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Gerencia uma lista de assemblies que são carregados pelo CLR e não pelo host.  
  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Fornece métodos para o host acessar e configurar vários aspectos do CLR.  
  
 [Interface ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Fornece métodos que permitem que um host associar um conjunto de tarefas com um identificador e um nome amigável.  
  
 [Interface ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Fornece métodos que permitem que o host configurar despejos de heap personalizado para o relatório de erros.  
  
 [Interface ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Fornece métodos que permitem que um host interagir com o sistema de coleta de lixo do CLR.  
  
 [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Fornece métodos para o host avaliar e comunicar as alterações nas informações de política para assemblies.  
  
 [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Permite que o host ao bloquear classes gerenciadas específicas, métodos, propriedades e campos da execução em código parcialmente confiável.  
  
 [Interface ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementa um método de retorno de chamada que permite que o host notificar o CLR do status de solicitações de e/s especificados.  
  
 [Interface ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Permite que o host de condições de pressão de memória de relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.  
  
 [Interface ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Fornece métodos que permitem que o host para se registrar e cancelar o registro de retornos de chamada para eventos de CLR.  
  
 [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Fornece métodos que permitem que o host especificar ações de política a ser executada no caso de falhas e tempos limite.  
  
 [Interface ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o CLR, sem a necessidade de criar ou entender essa identidade.  
  
 [Interface ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Fornece métodos que permitem que o host manipular o conjunto de assemblies referenciados por um arquivo ou fluxo usando os dados de identidade do assembly que é internos para o CLR, sem a necessidade de criar ou entender essas identidades.  
  
 [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Fornece recursos semelhantes aos [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), com um método adicional para definir a interface de controle de host.  
  
 [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Fornece métodos para o host para obter informações sobre tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.  
  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Fornece métodos que permitem que o host para fazer solicitações do CLR, ou para fornecer uma notificação para o CLR sobre a tarefa associada.  
  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Fornece métodos que permitem que o host solicitar explicitamente que o CLR cria uma nova tarefa, obter a tarefa em execução no momento e definir o idioma geográfico e a cultura para a tarefa.  
  
 [Interface ICLRValidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Fornece métodos para validar as imagens portáteis executáveis (PE) e relatando erros de validação.  
  
 [Interface ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Fornece métodos para configurar o CLR.  
  
 [Interface ICorThreadpool](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Fornece métodos para acessar o pool de threads.  
  
 [Interface IDebuggerInfo](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Fornece métodos para obter informações sobre o estado dos serviços de depuração.  
  
 [Interface IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Fornece métodos para notificar o host sobre o bloqueio e desbloqueio de segmentos pelos serviços de depuração.  
  
 [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.  
  
 [Interface IGCHost2](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Fornece o [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) método que permite que um host definir o tamanho do segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo zero com valores maiores que `DWORD`.  
  
 [Interface IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Fornece um método que permite que o coletor de lixo solicitar o host para alterar os limites de memória virtual.  
  
 [Interface IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Fornece métodos para a participação no agendamento de threads que, caso contrário, seriam bloqueados para coleta de lixo.  
  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Fornece métodos que permitem que um host ao especificar conjuntos de assemblies que devem ser carregados pelo CLR ou pelo host.  
  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Fornece métodos que permitem que um host carregar assemblies e módulos independentemente do CLR.  
  
 [Interface IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Fornece uma representação de um evento de redefinição automática implementado pelo host.  
  
 [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Fornece métodos para configurar o carregamento de assemblies e para determinar quais hospedando interfaces o oferece suporte ao host.  
  
 [Interface IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Serve como a representação do host de uma seção crítica para threading.  
  
 [Interface IHostGCManager](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Fornece métodos que notificar o host de eventos no mecanismo de coleta de lixo implementado pelo CLR.  
  
 [Interface IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Fornece métodos que permitem que o CLR interagir com as portas de conclusão de e/s fornecidas pelo host.  
  
 [Interface IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Fornece métodos para o CLR solicitar refinadas alocações do heap por meio do host.  
  
 [Interface IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Fornece a implementação do host de uma representação de um evento de redefinição manual.  
  
 [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Fornece métodos para o CLR fazer solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual padrão do Win32.  
  
 [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Fornece métodos que notificar o host das ações o CLR executa no caso de for anulada, tempos limites ou falhas.  
  
 [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Permite que o CLR manter informações de contexto de segurança implementadas pelo host.  
  
 [Interface IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Fornece métodos que permitem o acesso ao e controlam sobre o contexto de segurança do thread em execução no momento.  
  
 [Interface IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Fornece uma representação de um semáforo implementado pelo host.  
  
 [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Fornece métodos para o CLR criar primitivos de sincronização chamando-se o host, em vez de usar as funções de sincronização do Win32.  
  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Fornece métodos que permitem que o CLR para se comunicar com o host para gerenciar tarefas.  
  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Fornece métodos que permitem que o CLR trabalhar com tarefas por meio do host em vez de usar as funções de threading ou fibra do sistema operacional padrão.  
  
 [Interface IHostThreadPoolManager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Fornece métodos para o CLR para configurar o pool de threads e para enfileirar itens de trabalho para o pool de threads.  
  
 [Interface IManagedObject](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Fornece métodos para controlar um objeto gerenciado.  
  
 "IObjectHandle"  
 Fornece um método para descodificar objetos marshal-by-value de uma indireção.  
  
 [Interface ITypeName](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Fornece métodos para obter informações de nome de tipo. (Esta interface dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.)  
  
 [Interface ITypeNameBuilder](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Fornece métodos para a criação de um nome de tipo. (Esta interface dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.)  
  
 [Interface ITypeNameFactory](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Fornece métodos para desconstruir um nome de tipo. (Esta interface dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.)  
  
 "IValidator"  
 Fornece métodos para validar as imagens portáteis executáveis (PE) e relatando erros de validação.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces e coclasses de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework versão 1.0 e 1.1.  
  
 [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework 4.
