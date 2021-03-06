---
title: <certificateReference>fins<identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 93a6290d780ff61756f7315cd0c32f0e199ca00f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849989"
---
# <a name="certificatereference-for-identity"></a>\<> certificateReference para \<> de identidade
Especifica as configurações para a validação de certificado X. 509. Um cliente de Windows Communication Foundation seguro (WCF) que se conecta a um ponto de extremidade com essa identidade verifica se as declarações apresentadas pelo servidor contêm a declaração de identidade usada para construir essa identidade.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de identidade**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certificateReference**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|findValue|Especifica o valor a ser procurado no repositório de certificados X. 509. O tipo contido neste atributo deve atender aos requisitos do valor especificado `X509FindType` . O padrão é uma cadeia de caracteres vazia.|  
|isChainIncluded|Um valor booliano que especifica se a validação é feita usando uma cadeia de certificados.|  
|storeLocation|Especifica o local do repositório de certificados que o cliente pode usar para validar o certificado do servidor.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> LocalMachine O repositório de certificados atribuído ao computador local.<br />CurrentUser O repositório de certificados atribuído ao usuário atual.<br /><br /> O valor padrão é LocalMachine.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
|storeName|Especifica o nome do repositório de certificados X.509 a ser aberto.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> Catálogo Repositório de certificados para outros usuários.<br />- AuthRoot: Repositório de certificados para CAs (autoridades de certificação) de terceiros.<br />CertificateAuthority Repositório de certificados para CAs intermediárias.<br />Permitida Repositório de certificados para certificados revogados.<br />Pasta Repositório de certificados para certificados pessoais.<br />Básica Repositório de certificados para autoridades de certificação raiz confiáveis.<br />TrustedPeople Repositório de certificados para pessoas e recursos diretamente confiáveis.<br />- TrustedPublisher: Repositório de certificados para editores diretamente confiáveis.<br /><br /> O valor padrão é My.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreName>.|  
|X509FindType|Especifica o tipo de pesquisa X. 509 a ser executada. O tipo contido no `findValue` atributo deve atender aos requisitos do X509FindType especificado.<br /><br /> Os valores válidos incluem o seguinte:<br /><br /> -   FindByThumbPrint<br />-FindBySubjectName<br />- FindBySubjectDistinguishedName<br />- FindByIssuerName<br />- FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />- FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />- FindByApplicationPolicy<br />- FindByCertificatePolicy<br />- FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> O valor padrão é FindBySubjectDistinguishedName.<br /><br /> Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509FindType>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Especifica as configurações que habilitam a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
