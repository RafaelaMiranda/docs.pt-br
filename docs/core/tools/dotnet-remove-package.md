---
title: Comando dotnet remove package
description: O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632428"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.

## <a name="synopsis"></a>Sinopse

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica o arquivo do projeto. Se não for especificado, o comando pesquisará um no diretório atual.

`PACKAGE_NAME`

A referência de pacote a ser removida.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

## <a name="examples"></a>Exemplos

Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:

`dotnet remove package Newtonsoft.Json`
