---
title: Instrução Enum (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: be1780b00b4d58964e1de5ec199cb80dc0f9dba5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583402"
---
# <a name="enum-statement-visual-basic"></a>Instrução Enum (Visual Basic)

Declara uma enumeração e define os valores de seus membros.

## <a name="syntax"></a>Sintaxe

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a>Partes

- `attributelist`

  Opcional. Lista de atributos que se aplicam a essa enumeração. Você deve colocar a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`" e "`>`").

  O atributo <xref:System.FlagsAttribute> indica que o valor de uma instância da enumeração pode incluir vários membros de enumeração e que cada membro representa um campo de bits no valor de enumeração.

- `accessmodifier`

  Opcional. Especifica qual código pode acessar essa enumeração. Pode ser um dos seguintes:

  - [Público](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Privado](../../../visual-basic/language-reference/modifiers/private.md)

  - [Amigo Protegido](../../language-reference/modifiers/protected-friend.md)

  - [Particular Protegido](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  Opcional. Especifica que essa enumeração redeclara e oculta um elemento de programação nomeado de forma idêntica, ou conjunto de elementos sobrecarregados, em uma classe base. Você pode especificar [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) apenas na enumeração, não em nenhum de seus membros.

- `enumerationname`

  Necessário. Nome da enumeração. Para obter informações sobre nomes válidos, consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `datatype`

  Opcional. Tipo de dados da enumeração e todos os seus membros.

- `memberlist`

  Necessário. Lista de constantes de membro sendo declarada nesta instrução. Vários membros aparecem em linhas de código-fonte individuais.

  Cada `member` tem a seguinte sintaxe e partes: `[<attribute list>] member name [ = initializer ]`

  |Parte|Descrição|
  |---|---|
  |`membername`|Necessário. Nome deste membro.|
  |`initializer`|Opcional. Expressão que é avaliada em tempo de compilação e atribuída a este membro.|

- `End` `Enum`

  Encerra o bloco de `Enum`.

## <a name="remarks"></a>Comentários

Se você tiver um conjunto de valores inalteráveis logicamente relacionados entre si, você poderá defini-los juntos em uma enumeração. Isso fornece nomes significativos para a enumeração e seus membros, que são mais fáceis de lembrar do que seus valores. Você pode usar os membros de enumeração em muitos locais em seu código.

Os benefícios do uso de enumerações incluem o seguinte:

- Reduz os erros causados pela transposição ou números incorretas de digitação.

- Torna mais fácil alterar valores no futuro.

- Torna o código mais fácil de ler, o que significa que é menos provável que os erros sejam introduzidos.

- Garante a compatibilidade com o futuro. Se você usar enumerações, o código terá menos probabilidade de falhar se, em outras pessoas, alterar os valores correspondentes aos nomes dos membros.

Uma enumeração tem um nome, um tipo de dados subjacente e um conjunto de membros. Cada membro representa uma constante.

Uma enumeração declarada na classe, estrutura, módulo ou nível de interface, fora de qualquer procedimento, é uma *enumeração de membro*. É um membro da classe, da estrutura, do módulo ou da interface que o declara.

As enumerações de membro podem ser acessadas de qualquer lugar dentro de sua classe, estrutura, módulo ou interface. O código fora de uma classe, estrutura ou módulo deve qualificar o nome de uma enumeração de membro com o nome dessa classe, estrutura ou módulo. Você pode evitar a necessidade de usar nomes totalmente qualificados adicionando uma instrução [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ao arquivo de origem.

Uma enumeração declarada no nível de namespace, fora de qualquer classe, estrutura, módulo ou interface, é um membro do namespace no qual ela aparece.

O *contexto de declaração* para uma enumeração deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface, e não pode ser um procedimento. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Você pode aplicar atributos a uma enumeração como um todo, mas não a seus membros individualmente. Um atributo contribui com informações para os metadados do assembly.

## <a name="data-type"></a>Tipo de dados

A instrução `Enum` pode declarar o tipo de dados de uma enumeração. Cada membro usa o tipo de dados da enumeração. Você pode especificar `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong` ou `UShort`.

Se você não especificar `datatype` para a enumeração, cada membro usará o tipo de dados de seu `initializer`. Se você especificar `datatype` e `initializer`, o tipo de dados de `initializer` deverá ser conversível para `datatype`. Se nem `datatype` nem `initializer` estiverem presentes, o tipo de dados padrão será `Integer`.

## <a name="initializing-members"></a>Inicializando Membros

A instrução `Enum` pode inicializar o conteúdo dos membros selecionados em `memberlist`. Você usa `initializer` para fornecer uma expressão a ser atribuída ao membro.

Se você não especificar `initializer` para um membro, Visual Basic o inicializará como zero (se for o primeiro `member` no `memberlist`) ou com um valor maior que o de `member` imediatamente anterior.

A expressão fornecida em cada `initializer` pode ser qualquer combinação de literais, outras constantes que já estão definidas e membros de enumeração que já estão definidos, incluindo um membro anterior dessa enumeração. Você pode usar operadores aritméticos e lógicos para combinar esses elementos.

Você não pode usar variáveis ou funções no `initializer`. No entanto, você pode usar palavras-chave de conversão, como `CByte` e `CShort`. Você também pode usar `AscW` se chamá-lo com uma constante `String` ou `Char` argumento, pois isso pode ser avaliado no momento da compilação.

Enumerações não podem ter valores de ponto flutuante. Se um membro recebe um valor de ponto flutuante e `Option Strict` é definido como on, ocorre um erro do compilador. Se `Option Strict` for off, o valor será convertido automaticamente para o tipo de `Enum`.

Se o valor de um membro exceder o intervalo permitido para o tipo de dados subjacente, ou se você inicializar qualquer membro para o valor máximo permitido pelo tipo de dados subjacente, o compilador relatará um erro.

## <a name="modifiers"></a>Modificadores

Enumerações de classe, estrutura, módulo e membro de interface padrão para acesso público. Você pode ajustar seus níveis de acesso com os modificadores de acesso. Enumerações de membro de namespace padrão para Friend Access. Você pode ajustar seus níveis de acesso para público, mas não para privado ou protegido. Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Todos os membros de enumeração têm acesso público e você não pode usar nenhum modificador de acesso neles. No entanto, se a enumeração tiver um nível de acesso mais restrito, o nível de acesso de enumeração especificado terá precedência.

Por padrão, todas as enumerações são tipos e seus campos são constantes. Portanto, as palavras-chave `Shared`, `Static` e `ReadOnly` não podem ser usadas ao declarar uma enumeração ou seus membros.

## <a name="assigning-multiple-values"></a>Atribuindo vários valores

Enumerações normalmente representam valores mutuamente exclusivos. Ao incluir o atributo <xref:System.FlagsAttribute> na declaração `Enum`, você pode atribuir vários valores a uma instância da enumeração. O atributo <xref:System.FlagsAttribute> especifica que a enumeração seja tratada como um campo de bits, ou seja, um conjunto de sinalizadores. Elas são chamadas de enumerações *bit* -ais.

Ao declarar uma enumeração usando o atributo <xref:System.FlagsAttribute>, recomendamos que você use potências de 2, ou seja, 1, 2, 4, 8, 16 e assim por diante, para os valores. Também recomendamos que "None" seja o nome de um membro cujo valor é 0. Para obter diretrizes adicionais, consulte <xref:System.FlagsAttribute> e <xref:System.Enum>.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar a instrução `Enum`. Observe que o membro é conhecido como `EggSizeEnum.Medium`, e não como `Medium`.

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a>Exemplo

O método no exemplo a seguir está fora da classe `Egg`. Portanto, `EggSizeEnum` é totalmente qualificado como `Egg.EggSizeEnum`.

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a>Exemplo

O exemplo a seguir usa a instrução `Enum` para definir um conjunto relacionado de valores constantes nomeados. Nesse caso, os valores são cores que você pode optar por criar formulários de entrada de dados para um banco de dado.

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a>Exemplo

O exemplo a seguir mostra valores que incluem números positivos e negativos.

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a>Exemplo

No exemplo a seguir, uma cláusula `As` é usada para especificar o `datatype` de uma enumeração.

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar uma enumeração de bits. Vários valores podem ser atribuídos a uma instância de uma enumeração bit a bit. A declaração de `Enum` inclui o atributo <xref:System.FlagsAttribute>, que indica que a enumeração pode ser tratada como um conjunto de sinalizadores.

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a>Exemplo

O exemplo a seguir itera por meio de uma enumeração. Ele usa o método <xref:System.Enum.GetNames%2A> para recuperar uma matriz de nomes de membro da enumeração e <xref:System.Enum.GetValues%2A> recuperar uma matriz de valores de membro.

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a>Consulte também

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Constantes e Enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)
