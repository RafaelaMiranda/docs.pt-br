---
title: Método ICorProfilerObjectEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08b3d9634362d47615fe14287ab9ec35e78ee65
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775050"
---
# <a name="icorprofilerobjectenumgetcount-method"></a>Método ICorProfilerObjectEnum::GetCount
Obtém o número total de objetos congelados na coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pcelt`  
 [out] Um ponteiro para o número de objetos congelados na coleção.  
  
 Esse método sempre retornará zero no .NET Framework versão 3.5 Service Pack 1 (SP1) e versões posteriores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
