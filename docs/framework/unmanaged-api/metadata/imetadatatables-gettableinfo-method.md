---
title: Método IMetaDataTables::GetTableInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4844834232e34ab5dacfa34e7aa5d204ee344612
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781352"
---
# <a name="imetadatatablesgettableinfo-method"></a>Método IMetaDataTables::GetTableInfo
Obtém o nome, tamanho da linha, número de linhas, o número de colunas e o índice da coluna de chave da tabela especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ixTbl`  
 [in] O identificador da tabela cujas propriedades a serem retornadas.  
  
 `pcbRow`  
 [out] Um ponteiro para o tamanho, em bytes, de uma linha da tabela.  
  
 `pcRows`  
 [out] Um ponteiro para o número de linhas na tabela.  
  
 `pcCols`  
 [out] Um ponteiro para o número de colunas na tabela.  
  
 `piKey`  
 [out] Um ponteiro para o índice da coluna de chave, ou -1 se a tabela não tiver nenhuma coluna de chave.  
  
 `ppName`  
 [out] Um ponteiro para um ponteiro para o nome da tabela.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
