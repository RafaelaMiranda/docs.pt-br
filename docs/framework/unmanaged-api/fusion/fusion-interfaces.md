---
title: Interfaces de fusão
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605605f8510f7ccf5f0bbf2f3f6b09050a16025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795306"
---
# <a name="fusion-interfaces"></a>Interfaces de fusão
Esta seção descreve as interfaces não gerenciadas que a API do Fusion usa para acessar as propriedades dos recursos de um aplicativo e localizar as versões corretas desses recursos para o aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IAppIdAuthority](iappidauthority-interface.md)  
 Fornece métodos que geram e comparam chaves para identidades e referências de aplicativos.  
  
 [Interface IAssemblyCache](iassemblycache-interface.md)  
 Fornece uma representação do cache de assembly global.  
  
 [Interface IAssemblyCacheItem](iassemblycacheitem-interface.md)  
 Representa um único assembly no cache de assembly global.  
  
 [Interface IAssemblyEnum](iassemblyenum-interface.md)  
 Representa um enumerador para uma matriz `IAssemblyName` de objetos.  
  
 [Interface IAssemblyName](iassemblyname-interface.md)  
 Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.  
  
 [Interface IDefinitionAppId](idefinitionappid-interface.md)  
 Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.  
  
 [Interface IDefinitionIdentity](idefinitionidentity-interface.md)  
 Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.  
  
 [Interface IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md)  
 Serve como o enumerador para uma coleção `IDefinitionIdentity` de objetos.  
  
 [Interface IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md)  
 Serve como um enumerador para os atributos do objeto de código no escopo atual.  
  
 [Interface IEnumReferenceIdentity](ienumreferenceidentity-interface.md)  
 Serve como um enumerador para uma coleção `IReferenceIdentity` de objetos.  
  
 [Interface IIdentityAuthority](iidentityauthority-interface.md)  
 Gerencia chaves de identidade para objetos de código.  
  
 [Interface IInstallReferenceEnum](iinstallreferenceenum-interface.md)  
 Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.  
  
 [Interface IInstallReferenceItem](iinstallreferenceitem-interface.md)  
 Representa um item instalado no cache de assembly global.  
  
 [Interface IReferenceAppId](ireferenceappid-interface.md)  
 Representa uma referência ao identificador exclusivo para o aplicativo no escopo atual.  
  
 [Interface IReferenceIdentity](ireferenceidentity-interface.md)  
 Representa uma referência à assinatura exclusiva de um objeto de código.  
  
## <a name="reference"></a>Referência  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Funções estáticas globais de fusão](fusion-global-static-functions.md)  
  
 [Enumerações de fusão](fusion-enumerations.md)  
  
 [Estruturas de fusão](fusion-structures.md)
