---
title: Carregamento de dependência-.NET Core
description: Visão geral do carregamento de dependências gerenciadas e não gerenciadas no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 0388bd1fa29ce1caad93c917503dac9eed8974e1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926395"
---
# <a name="dependency-loading-in-net-core"></a>Carregamento de dependência no .NET Core

Cada aplicativo .NET Core tem dependências. Até mesmo o `hello world` aplicativo simples tem dependências em partes das bibliotecas de classes do .NET Core.

Entender a lógica de carregamento do assembly padrão do .NET Core pode ajudar a entender e depurar problemas de implantação típicos.

Em alguns aplicativos, as dependências são determinadas dinamicamente no tempo de execução. Nessas situações, é essencial entender como os assemblies gerenciados e as dependências não gerenciadas são carregados.

## <a name="understanding-assemblyloadcontext"></a>Entendendo o AssemblyLoadContext

A <xref:System.Runtime.Loader.AssemblyLoadContext> API é fundamental para o design de carregamento do .NET Core. O artigo [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) fornece uma visão geral conceitual do design.

## <a name="loading-details"></a>Carregando detalhes

Os detalhes do algoritmo de carregamento são abordados brevemente em vários artigos:

- [Algoritmo de carregamento de assembly gerenciado](loading-managed.md)
- [Algoritmo de carregamento de assembly satélite](loading-resources.md)
- [Algoritmo de carregamento de biblioteca não gerenciada (nativa)](loading-unmanaged.md)
- [Investigação padrão](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Criar um aplicativo do .NET Core com plug-ins

O tutorial [criar um aplicativo .NET Core com plug-ins](../tutorials/creating-app-with-plugin-support.md) descreve como criar um AssemblyLoadContext personalizado. Ele usa um <xref:System.Runtime.Loader.AssemblyDependencyResolver> para resolver as dependências do plug-in. O tutorial isola corretamente as dependências do plug-in do aplicativo de hospedagem.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Como usar e depurar a capacidade de descarregamento de assembly no .NET Core

O artigo [como usar e depurar a descarga do assembly no .NET Core](../../standard/assembly/unloadability-howto.md) é um tutorial passo a passo. Ele mostra como carregar um aplicativo .NET Core, executá-lo e descarregá-lo. O artigo também fornece dicas de depuração.
