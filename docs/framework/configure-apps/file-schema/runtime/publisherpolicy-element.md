---
title: Elemento <publisherPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252374"
---
# <a name="publisherpolicy-element"></a>\<Elemento de > publisherPolicy Apply
Especifica se o tempo de execução aplica a política do editor.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> assemblyBinding**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> publisherPolicy Apply**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`apply`|Especifica se a política do Publicador deve ser aplicada.|  
  
## <a name="apply-attribute"></a>aplicar atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`yes`|Aplica a política do Publicador. Essa é a configuração padrão.|  
|`no`|Não aplica a política do Publicador.|  
  
### <a name="child-elements"></a>Elementos filho  

nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`assemblyBinding`|Contém informações sobre o redirecionamento de versão e os locais dos assemblies.|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`dependentAssembly`|Encapsula local do assembly e política de associação para cada assembly. Use um `<dependentAssembly>` elemento para cada assembly.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Quando um fornecedor de componentes libera uma nova versão de um assembly, o fornecedor pode incluir uma política de editor para que os aplicativos que usam a versão antiga agora usem a nova versão. Para especificar se a política de editor deve ser aplicada a um determinado assembly, coloque o  **\<elemento publisherPolicy Apply >** no  **\<elemento dependentAssembly >** .  
  
 A configuração padrão para o atributo **aplicar** é **Sim**. A definição do atributo **aplicar** como **não** substitui as configurações **Sim** anteriores para um assembly.  
  
 A permissão é necessária para que um aplicativo ignore explicitamente a política do Publicador usando o [ \<elemento publisherPolicy Apply Apply = "no"/>](publisherpolicy-element.md) no arquivo de configuração do aplicativo. A permissão é concedida definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador <xref:System.Security.Permissions.SecurityPermission>no. Para obter mais informações, consulte permissão de segurança de redirecionamento de [Associação de assembly](../../assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desativa a política do Publicador para `myAssembly`o assembly,.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Como o tempo de execução localiza assemblies](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Redirecionando versões de assembly](../../redirect-assembly-versions.md)
