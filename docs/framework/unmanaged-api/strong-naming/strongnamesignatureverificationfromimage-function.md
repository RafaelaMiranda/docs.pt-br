---
title: Função StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22339b7d48e89f99d1500cfdda53f00f1234b80
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799069"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>Função StrongNameSignatureVerificationFromImage
Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbBase`  
 no O endereço virtual relativo do manifesto do assembly mapeado.  
  
 `dwLength`  
 no O tamanho, em bytes, da imagem mapeada.  
  
 `dwInFlags`  
 no Sinalizadores que influenciam o comportamento da verificação. Há suporte para os seguintes valores:  
  
- `SN_INFLAG_FORCE_VER`(0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.  
  
- `SN_INFLAG_INSTALL`(0x00000002) – especifica que esta é a primeira verificação executada nesta imagem.  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008) – especifica que o assembly será acessível somente para o usuário atual.  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010) – especifica que o cache não oferecerá nenhuma garantia de restrição de acesso.  
  
- `SN_INFLAG_RUNTIME`(0x80000000)-reservado para depuração interna.  
  
 `pdwOutFlags`  
 fora Um sinalizador para informações de saída adicionais. Há suporte para o seguinte valor:  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido a configurações do registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`após a conclusão bem-sucedida; caso contrário `false`,.  
  
## <a name="remarks"></a>Comentários  
 Se a `StrongNameSignatureVerificationFromImage` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameSignatureVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
