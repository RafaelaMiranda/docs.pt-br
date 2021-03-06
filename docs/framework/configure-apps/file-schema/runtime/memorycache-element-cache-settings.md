---
title: Elemento <memoryCache> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 25467fc751ad772e74ca714e6059bc5134300ed6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252478"
---
# <a name="memorycache-element-cache-settings"></a>\<Elemento de > memoryCache (configurações de cache)
Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>. A <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> classe define um elemento [MemoryCache](memorycache-element-cache-settings.md) que você pode usar para configurar o cache. Várias instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser usadas em um único aplicativo. Cada `memoryCache` elemento no arquivo de configuração pode conter configurações para uma instância <xref:System.Runtime.Caching.MemoryCache> nomeada.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> memoryCache**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>Tipo  
 <xref:System.Runtime.Caching.MemoryCache>classes.  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|O tamanho máximo da memória, em megabytes, que uma instância de <xref:System.Runtime.Caching.MemoryCache> um objeto pode aumentar para. O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.|  
|`Name`|O nome da configuração de cache.|  
|`PhysicalMemoryLimitPercentage`|A porcentagem de memória física que pode ser usada pelo cache. O valor padrão é 0, o que significa que <xref:System.Runtime.Caching.MemoryCache> a heurística de dimensionamento automático da classe é usada por padrão.|  
|`PollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache. O valor é inserido no formato "HH: MM: SS".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contém um conjunto de definições de configuração para a instância `namedCache`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Contém tipos que permitem implementar o cache de saída em aplicativos que são criados no .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
 A <xref:System.Runtime.Caching.MemoryCache> classe é uma implementação concreta da classe abstrata <xref:System.Runtime.Caching.ObjectCache> . As instâncias da <xref:System.Runtime.Caching.MemoryCache> classe podem ser fornecidas com informações de configuração dos arquivos de configuração do aplicativo. A seção de configuração [MemoryCache](memorycache-element-cache-settings.md) contém `namedCaches` uma coleção de configuração.  
  
 Quando um objeto de cache baseado em memória é inicializado, ele primeiro tenta encontrar `namedCaches` uma entrada que corresponda ao nome no parâmetro que é passado para o construtor de cache de memória. Se uma `namedCaches` entrada for encontrada, as informações de gerenciamento de memória e sondagem serão recuperadas do arquivo de configuração.  
  
 Em seguida, o processo de inicialização determina se as entradas de configuração foram substituídas, usando a coleção opcional de pares de nome/valor de informações de configuração no construtor. Se você passar qualquer um dos valores a seguir na coleção de pares nome/valor, esses valores substituirão as informações obtidas do arquivo de configuração:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o nome do <xref:System.Runtime.Caching.MemoryCache> objeto como o nome do objeto de cache padrão, definindo o `name` atributo como "default".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryLimitPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que a <xref:System.Runtime.Caching.MemoryCache> heurística de dimensionamento automático é usada por padrão. A implementação de cache deve comparar a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
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

- <xref:System.Runtime.Caching.MemoryCache>
- [\<Elemento System. Runtime. Caching > (configurações de cache)](system-runtime-caching-element-cache-settings.md)
- [\<Elemento de > namedCaches (configurações de cache)](namedcaches-element-cache-settings.md)
