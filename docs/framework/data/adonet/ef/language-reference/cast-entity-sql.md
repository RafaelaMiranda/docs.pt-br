---
title: CONVERSÃO (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 385f9a8057ea6aa3637f7fae6fec79154ac625ba
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251240"
---
# <a name="cast-entity-sql"></a>CONVERSÃO (Entity SQL)
Converte uma expressão de um tipo de dados para outro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Qualquer expressão válida que seja conversível para `data_type`.  
  
 `data_type`  
 O tipo de dados fornecido pelo sistema de destino. Deve ser um tipo primitivo (escalar). O `data_type` usado depende do espaço da consulta. Se uma consulta é executada com o <xref:System.Data.EntityClient.EntityCommand>, o tipo de dados será um tipo definido no modelo conceitual. Para obter mais informações, consulte [especificação CSDL](csdl-specification.md). Se uma consulta é executada com o <xref:System.Data.Objects.ObjectQuery%601>, o tipo de dados será um tipo CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o mesmo valor que `data_type`.  
  
## <a name="remarks"></a>Comentários  
 A expressão de conversão tem semântica semelhante à expressão CONVERT do Transact-SQL. A expressão cast é usada para converter um valor de um tipo em um valor de outro tipo.  
  
```  
CAST( e as T )  
```  
  
 Se e for de algum tipo S, e S for conversível para T, a expressão anterior será uma expressão cast válida. T deve ser um tipo primitivo (escalar).  
  
 Os valores para as facetas de precisão de escala podem opcionalmente ser fornecidos ao converter para `Edm.Decimal`. Se não forem fornecidos explicitamente, os valores padrão para precisão e escala serão 18 e 0, respectivamente. Especificamente, as seguintes sobrecargas têm suporte para `Decimal`:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 O uso de uma expressão cast é considerado uma conversão explícita. Conversões explícitas podem truncar dados ou perder precisão.  
  
> [!NOTE]
> CAST tem suporte somente em tipos primitivos e tipos de membro de enumeração.  
  
## <a name="example"></a>Exemplo  
 A consulta [!INCLUDE[esql](../../../../../../includes/esql-md.md)] a seguir usa o operador cast para converter uma expressão de um tipo de dados para outro. A consulta é baseada no modelo de vendas AdventureWorks. Para compilar e executar essa consulta, siga estas etapas:  
  
1. Siga o procedimento em [como: Executar uma consulta que retorna os resultados](../how-to-execute-a-query-that-returns-primitivetype-results.md)de primitivatype.  
  
2. Passe a consulta a seguir como um argumento para o método `ExecutePrimitiveTypeQuery`:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de Entity SQL](entity-sql-reference.md)
