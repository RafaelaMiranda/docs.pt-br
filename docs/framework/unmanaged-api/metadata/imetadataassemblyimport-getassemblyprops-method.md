---
title: Método IMetaDataAssemblyImport::GetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec04588bd1cc21e585d89c734c152a86fb835b15
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772724"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>Método IMetaDataAssemblyImport::GetAssemblyProps
Obtém o conjunto de propriedades para o assembly com a assinatura de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mda`  
 [in]. O `mdAssembly` token de metadados que representa o assembly para o qual obter as propriedades.  
  
 `ppbPublicKey`  
 [out] Um ponteiro para a chave pública ou token de metadados.  
  
 `pcbPublicKey`  
 [out] O número de bytes na chave pública retornada.  
  
 `pulHashAlgId`  
 [out] Um ponteiro para o algoritmo usado para os arquivos no assembly de hash.  
  
 `szName`  
 [out] O nome simples do assembly.  
  
 `cchName`  
 [in] O tamanho, em caracteres largos, de `szName`.  
  
 `pchName`  
 [out] O número de caracteres largos, na verdade, é retornado no `szName`.  
  
 `pMetaData`  
 [out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.  
  
 `pdwAssemblyFlags`  
 [out] Sinalizadores que descrevem os metadados aplicados a um assembly. Esse valor é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
