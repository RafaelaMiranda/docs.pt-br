---
title: Método IMetaDataAssemblyImport::GetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f3883b0cd1b7aca6265b738eace483c81eb37b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760144"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>Método IMetaDataAssemblyImport::GetFileProps
Obtém as propriedades do arquivo com a assinatura de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mdf`  
 [in] O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.  
  
 `szName`  
 [out] O nome simples do arquivo.  
  
 `cchName`  
 [in] O tamanho, em caracteres largos, de `szName`.  
  
 `pchName`  
 [out] O número de caracteres largos, na verdade, é retornado no `szName`.  
  
 `ppbHashValue`  
 [out] Um ponteiro para o valor de hash. Isso é o hash, usando o algoritmo SHA-1, do arquivo.  
  
 `pcbHashValue`  
 [out] O número de caracteres largos no valor de hash retornado.  
  
 `pdwFileFlags`  
 [out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado a um arquivo. O valor de sinalizadores é uma combinação de um ou mais [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) valores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
