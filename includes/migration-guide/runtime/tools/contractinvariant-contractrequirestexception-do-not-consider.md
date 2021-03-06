---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237913"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant ou Contract.Requires\<TException> não consideram String.IsNullOrEmpty puro

|   |   |
|---|---|
|Detalhes|Para aplicativos direcionados ao .NET Framework 4.6.1, se o contrato invariável de <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> ou o contrato de pré-condição de <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> chamar o método <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>, o regravador emitirá o aviso do compilador CC1036: &quot;Chamada detectada ao método 'System.String.IsNullOrWhteSpace(System.String)' sem [Pure] no método.&quot; Esse é um aviso do compilador, e não um erro do compilador.|
|Sugestão|Esse comportamento foi abordado em [Problema nº 339 no GitHub](https://github.com/Microsoft/CodeContracts/issues/339). Para eliminar esse aviso, você pode baixar e compilar uma versão atualizada do código-fonte para a ferramenta de Contratos de Código no [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). As informações para download são encontradas no fim da página.|
|Escopo|Secundário|
|Versão|4.6.1|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
