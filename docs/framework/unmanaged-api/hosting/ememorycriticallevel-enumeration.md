---
title: Enumeração EMemoryCriticalLevel
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774224"
---
# <a name="ememorycriticallevel-enumeration"></a>Enumeração EMemoryCriticalLevel
Contém valores que indicam o impacto de uma falha quando uma alocação de memória específica foi solicitada, mas não pode ser atendida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eAppDomainCritical`|Indica que a alocação é fundamental para a execução de código gerenciado no domínio que solicitou a alocação. Se não é possível alocar memória, o CLR não garante que o domínio ainda é utilizável. O host decide qual ação será tomada quando a alocação não pode ser atendida. Ele pode instruir o CLR para anular a `AppDomain` automaticamente, ou permitir que ele continue em execução chamando métodos na [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Indica que a alocação é fundamental para a execução de código gerenciado no processo. Esse valor é usado durante a inicialização e quando a execução dos finalizadores. Se não é possível alocar memória, o CLR não pode operar no processo. Se a alocação falhar, o CLR estará efetivamente desabilitado. Todas as chamadas subsequentes para o CLR falharem com HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Indica que a alocação é fundamental para a execução da tarefa que solicitou a alocação. Se não é possível alocar memória, o CLR não garante que a tarefa pode ser executada. No caso de falha, o CLR aciona um <xref:System.Threading.ThreadAbortException> no thread de sistema de operação física.|  
  
## <a name="remarks"></a>Comentários  
 Os métodos de alocação de memória definidos na [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) e [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces utilizam um parâmetro desse tipo. Dependendo da gravidade de uma falha, um host pode decidir se fazer a solicitação de alocação imediatamente ou aguardar até que ele pode ser atendido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
