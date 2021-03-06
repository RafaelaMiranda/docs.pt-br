---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ac193b6b78434245b8f11a4f627b4e1992feb8a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661281"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>Método ICorProfilerInfo10:: EnumerateObjectReferences

Dado um ObjectID, retorno de chamada e clientData, enumera cada referência de objeto (se houver).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a>Parâmetros

`objectId` \
no O objeto no qual enumerar referências.

`callback` \
no A função que será chamada com as referências para o objeto.

`clientData` \
no Dados fornecidos pelo criador de perfil para passar `callback` para a função.

## <a name="remarks"></a>Comentários

O método `EnumerateObjectReferences` é semelhante a [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), exceto pelo fato de que ele percorre as referências sob demanda para o criador de perfil em vez de alocar previamente uma matriz para armazenar as referências.

## <a name="requirements"></a>Requisitos

**Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Cabeçalho:** CorProf.idl, CorProf.h

**Biblioteca** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
