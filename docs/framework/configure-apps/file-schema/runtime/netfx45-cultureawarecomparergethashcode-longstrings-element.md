---
title: Elemento <NetFx45_CultureAwareComparerGetHashCode_LongStrings>
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef814d1b5f32359033e8a19999d6271677315fff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252416"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a>\<Elemento de > NetFx45_CultureAwareComparerGetHashCode_LongStrings

Especifica se o tempo de execução usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<> NetFx45_CultureAwareComparerGetHashCode_LongStrings**  

## <a name="syntax"></a>Sintaxe

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o Common Language Runtime atribui uma quantidade fixa de memória ao calcular códigos hash.|

## <a name="enabled-attribute"></a>Atributo habilitado

|Valor|Descrição|
|-----------|-----------------|
|0|O Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash. Esse é o padrão.|
|1|O Common Language Runtime aloca uma quantidade fixa de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|

## <a name="remarks"></a>Comentários

Por padrão, o Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> e um <xref:System.ArgumentException> pode ser disparado quando o método tentar calcular o código hash de cadeias de caracteres muito grandes (com comprimentos superiores a vários milhões de caracteres). Ao adicionar esse elemento a um arquivo de configuração do aplicativo e definir seu atributo `enabled` como "1", você poderá especificar que o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> use um algoritmo alternativo que aloque uma quantidade fixa de memória para o cálculo de códigos hash.

> [!IMPORTANT]
> O elemento `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` não é usado em [!INCLUDE[win8](../../../../../includes/win8-md.md)] e versões posteriores.

## <a name="see-also"></a>Consulte também

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
