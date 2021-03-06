---
title: <message>elemento de<netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 0cf4f66df43070cc90443e3a640915df46a5cccd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400287"
---
# <a name="message-element-of-nettcpbinding"></a>\<elemento de > de \<mensagem de NetTcpBinding >
Define o tipo de requisitos de segurança no nível de mensagem para um ponto de extremidade configurado com o [ \<> NetTcpBinding](nettcpbinding.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> netTcpbinding**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de mensagem**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`algorithmSuite`|Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves. Os algoritmos e os tamanhos de chave são determinados <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> pela classe. Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).<br /><br /> Os valores possíveis são mostrados na tabela a seguir. O valor padrão é `Basic256`.<br /><br /> Se a associação de serviço especificar `algorithmSuite` um valor que não seja igual ao padrão, e você gerar o arquivo de configuração usando svcutil. exe, ele não será gerado corretamente e você deverá editar manualmente o arquivo de configuração para definir esse atributo como o valor desejado.|  
|`clientCredentialType`|Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente usando a segurança baseada em mensagem. Os valores possíveis são mostrados na tabela a seguir. O valor padrão é `UserName`. Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|  
  
## <a name="algorithmsuite-attribute"></a>Atributo algorithmSuite  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Basic128|Use criptografia Aes128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic192|Use a criptografia Aes192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic256|Use a criptografia Aes256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic256Rsa15|Use Aes256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.|  
|Basic192Rsa15|Use Aes192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.|  
|TripleDes|Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic128Rsa15|Use Aes128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.|  
|TripleDesRsa15|Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.|  
|Basic128Sha256|Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.|  
|Basic192Sha256|Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic256Sha256|Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.|  
|TripleDesSha256|Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.|  
|Basic128Sha256Rsa15|Use Aes128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
|Basic192Sha256Rsa15|Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
|Basic256Sha256Rsa15|Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra automática de chave.|  
|TripleDesSha256Rsa15|Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.|  
  
## <a name="clientcredentialtype-attribute"></a>Atributo clientCredentialtype  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|Isso permite que o serviço interaja com clientes anônimos. No serviço, isso indica que o serviço não requer nenhuma credencial de cliente. No cliente, isso indica que o cliente não fornece nenhuma credencial de cliente.|  
|Windows|Permite que as trocas SOAP estejam sob o contexto autenticado de uma credencial do Windows.|  
|UserName|Permite que o serviço exija que o cliente seja autenticado usando uma credencial de nome de usuário. O WCF não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando a senha e usando essas chaves para segurança de mensagem. Dessa forma, o WCF impõe que o transporte seja protegido ao usar credenciais de nome de usuário. Esse modo de credencial resulta em um intercâmbio interoperável ou em uma negociação não interoperável `negotiateServiceCredential` com base no atributo.|  
|Certificate|Permite que o serviço exija que o cliente seja autenticado usando um certificado. Se o modo de segurança da mensagem for `negotiateServiceCredential` usado e o atributo `false`for definido como, o cliente deverá ser provisionado com o certificado de serviço.|  
|IssuedToken|Especifica um token personalizado, geralmente emitido por um serviço de token de segurança (STS).|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|Define os recursos de segurança para <xref:System.ServiceModel.Configuration.NetTcpBindingElement>o.|  
  
## <a name="remarks"></a>Comentários  
 A mensagem usa segurança em nível de mensagem para a integridade e a confidencialidade da mensagem SOAP e para a autenticação mútua dos pares de comunicação. Se esse modo de segurança for selecionado em uma associação, a pilha de canais será configurada com elementos de ligação de segurança de mensagem e as mensagens SOAP serão protegidas em conformidade com os padrões WS-Security *.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
