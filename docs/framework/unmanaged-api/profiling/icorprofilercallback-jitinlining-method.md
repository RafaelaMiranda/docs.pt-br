---
title: Método ICorProfilerCallback::JITInlining
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782798"
---
# <a name="icorprofilercallbackjitinlining-method"></a>Método ICorProfilerCallback::JITInlining
Notifica o criador de perfil que o compilador just-in-time (JIT) está prestes a inserir uma função alinhada com outra função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `callerId`  
 [in] A ID da função na qual o `calleeId` função será inserida.  
  
 `calleeId`  
 [in] A ID da função a ser inserido.  
  
 `pfShouldInline`  
 [out] `true` para permitir a inserção ocorrer; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 O criador de perfil pode definir `pfShouldInline` à `false` para impedir que o `calleeId` função seja inserido no `callerId` função. Além disso, o criador de perfil pode desativar globalmente a inserção embutido usando o valor COR_PRF_DISABLE_INLINING a [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeração.  
  
 Funções inseridas embutido não acionar eventos para entrar ou sair. Portanto, o criador de perfil deve definir `pfShouldInline` para `false` para produzir um gráfico de chamadas de preciso. Definindo `pfShouldInline` para `false` afetará o desempenho, porque a inserção embutidos geralmente aumenta a velocidade e reduz o número de eventos de compilação JIT separados para o método inserido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
