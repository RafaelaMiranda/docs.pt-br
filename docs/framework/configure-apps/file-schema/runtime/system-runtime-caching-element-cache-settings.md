---
title: Elemento <system.runtime.caching> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e36e2ed96a0748a69f2bd9ee32432901f0bf0898
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252285"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<Elemento System. Runtime. Caching > (configurações de cache)

Fornece a configuração para a implementação padrão na <xref:System.Runtime.Caching.ObjectCache> memória por meio `memoryCache` da entrada no arquivo de configuração.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp; **\<sistema. Runtime. Caching >**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos

`None`  

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.|  
  
## <a name="remarks"></a>Comentários

As classes nesse namespace fornecem uma maneira de usar recursos de caching como aqueles em ASP.net, mas sem uma dependência no `System.Web` assembly. Para obter mais informações, consulte [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> A funcionalidade e os tipos de cache de <xref:System.Runtime.Caching> saída no namespace são novos no .NET Framework 4.  
  
## <a name="example"></a>Exemplo

O exemplo a seguir mostra como configurar um cache baseado na <xref:System.Runtime.Caching.MemoryCache> classe. O exemplo mostra como configurar uma instância da entrada para `namedCaches` o cache de memória. O nome do cache é definido como o nome da entrada de cache padrão, definindo `name` o atributo como "padrão".  
  
O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão. A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [\<Elemento de > memoryCache (configurações de cache)](memorycache-element-cache-settings.md)
