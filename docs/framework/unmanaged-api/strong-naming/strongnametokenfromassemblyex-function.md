---
title: Função StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c000aad12000a9c76fb6dd805a9b002c021be6ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798844"
---
# <a name="strongnametokenfromassemblyex-function"></a>Função StrongNameTokenFromAssemblyEx
Cria um token de nome forte a partir do arquivo de assembly especificado e retorna a chave pública que o token representa.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no O caminho para o arquivo executável portátil (PE) para o assembly.  
  
 `ppbStrongNameToken`  
 fora O token de nome forte retornado.  
  
 `pcbStrongNameToken`  
 fora O tamanho, em bytes, do token de nome forte.  
  
 `ppbPublicKeyBlob`  
 fora A chave pública retornada.  
  
 `pcbPublicKeyBlob`  
 fora O tamanho, em bytes, da chave pública.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`após a conclusão bem-sucedida; caso contrário `false`,.  
  
## <a name="remarks"></a>Comentários  
 Um token de nome forte é a forma abreviada de uma chave pública. O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly. O token é uma parte do nome forte para o assembly e pode ser lido nos metadados do assembly.  
  
 Depois que a chave for recuperada e o token for criado, você deverá chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.  
  
 Se a `StrongNameTokenFromAssemblyEx` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [Método StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
