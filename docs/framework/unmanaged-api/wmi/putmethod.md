---
title: Função PutMethod (referência de API não gerenciada)
description: A função PutMethod cria um método.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b41cbbade9da5c2095309b9039b8ce2758f6f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798355"
---
# <a name="putmethod-function"></a>Função PutMethod
Cria um método.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*  ptr, 
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
no Este parâmetro não é usado.

`ptr`  
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`  
no O nome do método a ser criado. 

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`pSignatureIn`  
no Um ponteiro para uma cópia da [classe de sistema __Parameters](/windows/desktop/WmiSdk/--parameters) que contém os `in` parâmetros para o método. Esse parâmetro será ignorado se for definido `null`como.  

`pSignatureOut`  
no  Um ponteiro para uma cópia da [classe de sistema __Parameters](/windows/desktop/WmiSdk/--parameters) que contém os `out` parâmetros para o método. Esse parâmetro será ignorado se for definido `null`como.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | O `[in, out]` parâmetro do método especificado nos objetos *pInSignature* e *pOutSignature* tem qualificadores diferentes.
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | Um parâmetro de método não tem a especificação do qualificador de **ID** . |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | A série de IDs atribuída aos parâmetros do método não é consecutiva ou não começa em 0. |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | O valor de retorno para um método tem um qualificador de **ID** . |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | Foi feita uma tentativa de reutilizar um nome de método existente de uma classe pai e as assinaturas não corresponderam. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

Esta chamada de método só terá suporte `ptr` se for uma definição de classe CIM. A manipulação de método não está disponível em ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias CIM.

Os usuários não podem criar métodos com nomes que comecem ou terminem com um sublinhado. Isso é reservado para classes e propriedades do sistema.

Para um método, os `in` parâmetros `out` e são descritos como propriedades em objetos [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Um `[in/out]` parâmetro pode ser definido adicionando a mesma propriedade aos dois objetos apontados `pInSignature` pelos parâmetros e `pOutSignature` . Nesse caso, as propriedades compartilham o mesmo valor de qualificador de **ID** .

Cada propriedade em um objeto de classe [__Parameters](/windows/desktop/WmiSdk/--parameters) diferente `ReturnValue` de deve ter um qualificador de **ID** , um valor numérico com base em zero que identifica a ordem na qual os parâmetros são exibidos. Dois parâmetros não podem ter o mesmo valor de **ID** e nenhum valor de **ID** pode ser ignorado. Se qualquer condição ocorrer, a `PutMethod` função retornará `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.

## <a name="example"></a>Exemplo

Para obter um exemplo, consulte o método [IWbemClassObject::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .

## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
