---
title: Método ICorProfilerCallback::ModuleAttachedToAssembly
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3345e2e87ba41f750031deed2d15e13dbe4f06c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769297"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>Método ICorProfilerCallback::ModuleAttachedToAssembly
Notifica o criador de perfil que um módulo está sendo anexado ao seu assembly pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo que está sendo anexado.  
  
 `AssemblyId`  
 [in] A ID do assembly pai ao qual o módulo está anexado.  
  
## <a name="remarks"></a>Comentários  
 Um módulo pode ser carregado por meio de uma importação endereço IAT (tabela), por meio de uma chamada para `LoadLibrary`, ou por meio de uma referência de metadados. Como resultado, o carregador de runtime (CLR) de linguagem comum tem vários caminhos de código para determinar o assembly no qual reside um módulo. Portanto, é possível que, depois [ICorProfilerCallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) é chamado, o módulo não sabe qual assembly esteja em e não é possível obter a ID do assembly pai. O `ModuleAttachedToAssembly` método é chamado quando o módulo está conectado ao seu assembly pai e seu assembly pai ID pode ser obtida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
