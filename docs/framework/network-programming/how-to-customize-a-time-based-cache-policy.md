---
title: 'Como: Personalizar uma política de cache baseada em tempo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: c28c6daf9b873a19291b1636112eae6546412be2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048322"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Como: Personalizar uma política de cache baseada em tempo
Ao criar uma política de cache baseada em tempo, você pode personalizar o comportamento do cache especificando valores para a idade máxima, atualização mínima, desatualização máxima ou data de sincronização do cache. O objeto <xref:System.Net.Cache.HttpRequestCachePolicy> fornece vários construtores que permitem especificar combinações válidas desses valores.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Para criar uma política de cache baseada em tempo que usa uma data de sincronização do cache  
  
- Crie uma política de cache baseada em tempo que usa uma data de sincronização do cache passando um objeto <xref:System.DateTime> para o construtor <xref:System.Net.Cache.HttpRequestCachePolicy>.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 A saída é semelhante à seguinte:  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Para criar uma política de cache baseada em tempo com base na atualização mínima  
  
- Crie uma política de cache baseada em tempo com base na atualização mínima especificando <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> como o valor de parâmetro `cacheAgeControl` e passando um objeto <xref:System.TimeSpan> para o construtor <xref:System.Net.Cache.HttpRequestCachePolicy>.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Para a seguinte invocação:  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 A saída é:
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Para criar uma política de cache baseada em tempo com base na atualização mínima e idade máxima  
  
- Crie uma política de cache baseada em tempo que tem como base a atualização mínima e a idade máxima especificando <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> como o valor do parâmetro `cacheAgeControl` e passando dois objetos <xref:System.TimeSpan> para o construtor <xref:System.Net.Cache.HttpRequestCachePolicy>, um para especificar a idade máxima dos recursos e um segundo para especificar a atualização mínima permitida para um objeto retornado do cache.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Para a seguinte invocação:  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

A saída é:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Consulte também

- [Gerenciamento de cache para aplicativos de rede](cache-management-for-network-applications.md)
- [Política de cache](cache-policy.md)
- [Políticas de cache baseadas na localização](location-based-cache-policies.md)
- [Políticas de cache baseadas em tempo](time-based-cache-policies.md)
- [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md) [Elemento requestCaching> (configurações de rede)]
