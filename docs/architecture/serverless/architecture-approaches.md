---
title: Abordagens de arquitetura-aplicativos sem servidor
description: Uma introdução às abordagens de arquitetura para a criação de aplicativos empresariais baseados em nuvem, desde arquiteturas de N camadas até servidores.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: ee529abd1f6955d4f542464dd9a2380dd663571f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577799"
---
# <a name="architecture-approaches"></a><span data-ttu-id="59ee7-103">Abordagens de arquitetura</span><span class="sxs-lookup"><span data-stu-id="59ee7-103">Architecture approaches</span></span>

<span data-ttu-id="59ee7-104">Entender as abordagens existentes para arquitetar aplicativos empresariais ajuda a esclarecer a função desempenhada por servidor.</span><span class="sxs-lookup"><span data-stu-id="59ee7-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="59ee7-105">Há muitas abordagens e padrões que evoluíram mais de décadas de desenvolvimento de software, e todos têm seus próprios prós e contras.</span><span class="sxs-lookup"><span data-stu-id="59ee7-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="59ee7-106">Em muitos casos, a solução definitiva pode não envolver a decisão de uma única abordagem, mas pode integrar várias abordagens.</span><span class="sxs-lookup"><span data-stu-id="59ee7-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="59ee7-107">Cenários de migração geralmente envolvem a mudança de uma abordagem de arquitetura para outra por meio de uma abordagem híbrida.</span><span class="sxs-lookup"><span data-stu-id="59ee7-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="59ee7-108">Este capítulo fornece uma visão geral dos padrões de arquitetura física e lógica para aplicativos empresariais.</span><span class="sxs-lookup"><span data-stu-id="59ee7-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="59ee7-109">Padrões de arquitetura</span><span class="sxs-lookup"><span data-stu-id="59ee7-109">Architecture patterns</span></span>

<span data-ttu-id="59ee7-110">Os aplicativos de negócios modernos seguem uma variedade de padrões de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="59ee7-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="59ee7-111">Esta seção representa uma pesquisa de padrões comuns.</span><span class="sxs-lookup"><span data-stu-id="59ee7-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="59ee7-112">Os padrões listados aqui não são necessariamente todas as práticas recomendadas, mas ilustram abordagens diferentes.</span><span class="sxs-lookup"><span data-stu-id="59ee7-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="59ee7-113">Para obter mais informações, consulte [Guia de arquitetura do aplicativo do Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="59ee7-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="59ee7-114">Monolitos</span><span class="sxs-lookup"><span data-stu-id="59ee7-114">Monoliths</span></span>

<span data-ttu-id="59ee7-115">Muitos aplicativos de negócios seguem um padrão monolítico.</span><span class="sxs-lookup"><span data-stu-id="59ee7-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="59ee7-116">Os aplicativos herdados são frequentemente implementados como monolíticos.</span><span class="sxs-lookup"><span data-stu-id="59ee7-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="59ee7-117">No padrão monolítico, todas as preocupações do aplicativo estão contidas em uma única implantação.</span><span class="sxs-lookup"><span data-stu-id="59ee7-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="59ee7-118">Tudo, desde a interface do usuário até chamadas de banco de dados, está incluído na mesma base de código.</span><span class="sxs-lookup"><span data-stu-id="59ee7-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Arquitetura monolítica](./media/monolith-architecture.png)

<span data-ttu-id="59ee7-120">Há várias vantagens para a abordagem monolítica.</span><span class="sxs-lookup"><span data-stu-id="59ee7-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="59ee7-121">Geralmente, é fácil puxar uma única base de código e começar a trabalhar.</span><span class="sxs-lookup"><span data-stu-id="59ee7-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="59ee7-122">O tempo de crescimento pode ser menor, e a criação de ambientes de teste é tão simples quanto fornecer uma nova cópia.</span><span class="sxs-lookup"><span data-stu-id="59ee7-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="59ee7-123">O monolítico pode ser projetado para incluir vários componentes e aplicativos.</span><span class="sxs-lookup"><span data-stu-id="59ee7-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="59ee7-124">Infelizmente, o padrão monolítico tende a dividir em escala.</span><span class="sxs-lookup"><span data-stu-id="59ee7-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="59ee7-125">As principais desvantagens da abordagem monolítica incluem:</span><span class="sxs-lookup"><span data-stu-id="59ee7-125">Major disadvantages of the monolith approach include:</span></span>

* <span data-ttu-id="59ee7-126">Difícil de trabalhar em paralelo na mesma base de código.</span><span class="sxs-lookup"><span data-stu-id="59ee7-126">Difficult to work in parallel in the same code base.</span></span>
* <span data-ttu-id="59ee7-127">Qualquer alteração, independentemente de como o trivial, exige a implantação de uma nova versão de todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59ee7-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
* <span data-ttu-id="59ee7-128">A refatoração afeta potencialmente o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="59ee7-128">Refactoring potentially impacts the entire application.</span></span>
* <span data-ttu-id="59ee7-129">Geralmente, a única solução a ser dimensionada é criar várias cópias com uso intensivo de recursos do monolítico.</span><span class="sxs-lookup"><span data-stu-id="59ee7-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
* <span data-ttu-id="59ee7-130">À medida que os sistemas expandem ou outros sistemas são adquiridos, a integração pode ser difícil.</span><span class="sxs-lookup"><span data-stu-id="59ee7-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
* <span data-ttu-id="59ee7-131">Pode ser difícil testar devido à necessidade de configurar todo o monolítico.</span><span class="sxs-lookup"><span data-stu-id="59ee7-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
* <span data-ttu-id="59ee7-132">A reutilização de código é desafiadora e, muitas vezes, outros aplicativos acabam tendo suas próprias cópias de código.</span><span class="sxs-lookup"><span data-stu-id="59ee7-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="59ee7-133">Muitas empresas procuram a nuvem como uma oportunidade de migrar aplicativos monolíticos e, ao mesmo tempo, refatorá-los para padrões mais utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="59ee7-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="59ee7-134">É comum dividir os aplicativos e componentes individuais para permitir que eles sejam mantidos, implantados e dimensionados separadamente.</span><span class="sxs-lookup"><span data-stu-id="59ee7-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="59ee7-135">Aplicativos de N camadas</span><span class="sxs-lookup"><span data-stu-id="59ee7-135">N-Layer applications</span></span>

<span data-ttu-id="59ee7-136">Lógica de aplicativo de partição de aplicativo de N camadas em camadas específicas.</span><span class="sxs-lookup"><span data-stu-id="59ee7-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="59ee7-137">As camadas mais comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="59ee7-137">The most common layers include:</span></span>

* <span data-ttu-id="59ee7-138">Interface do usuário</span><span class="sxs-lookup"><span data-stu-id="59ee7-138">User interface</span></span>
* <span data-ttu-id="59ee7-139">Lógica de negócios</span><span class="sxs-lookup"><span data-stu-id="59ee7-139">Business logic</span></span>
* <span data-ttu-id="59ee7-140">Acesso aos dados</span><span class="sxs-lookup"><span data-stu-id="59ee7-140">Data access</span></span>

<span data-ttu-id="59ee7-141">Outras camadas podem incluir middleware, processamento em lotes e API.</span><span class="sxs-lookup"><span data-stu-id="59ee7-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="59ee7-142">É importante observar que as camadas são lógicas.</span><span class="sxs-lookup"><span data-stu-id="59ee7-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="59ee7-143">Embora eles sejam desenvolvidos isoladamente, eles podem ser implantados na mesma plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="59ee7-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Arquitetura de N camadas](./media/n-layer-architecture.png)

<span data-ttu-id="59ee7-145">Há várias vantagens na abordagem de N camadas, incluindo:</span><span class="sxs-lookup"><span data-stu-id="59ee7-145">There are several advantages to the N-Layer approach, including:</span></span>

* <span data-ttu-id="59ee7-146">A refatoração é isolada em uma camada.</span><span class="sxs-lookup"><span data-stu-id="59ee7-146">Refactoring is isolated to a layer.</span></span>
* <span data-ttu-id="59ee7-147">As equipes podem criar, testar, implantar e manter camadas separadas de forma independente.</span><span class="sxs-lookup"><span data-stu-id="59ee7-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
* <span data-ttu-id="59ee7-148">As camadas podem ser trocadas, por exemplo, a camada de dados pode acessar vários bancos de dado sem a necessidade de alterações na camada da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="59ee7-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="59ee7-149">Sem servidor pode ser usado para implementar uma ou mais camadas.</span><span class="sxs-lookup"><span data-stu-id="59ee7-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="59ee7-150">Microsserviços</span><span class="sxs-lookup"><span data-stu-id="59ee7-150">Microservices</span></span>

<span data-ttu-id="59ee7-151">As arquiteturas de **[microserviços](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** contêm características comuns que incluem:</span><span class="sxs-lookup"><span data-stu-id="59ee7-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

* <span data-ttu-id="59ee7-152">Os aplicativos são compostos por vários serviços pequenos.</span><span class="sxs-lookup"><span data-stu-id="59ee7-152">Applications are composed of several small services.</span></span>
* <span data-ttu-id="59ee7-153">Cada serviço é executado em seu próprio processo.</span><span class="sxs-lookup"><span data-stu-id="59ee7-153">Each service runs in its own process.</span></span>
* <span data-ttu-id="59ee7-154">Os serviços são alinhados em relação a domínios de negócios.</span><span class="sxs-lookup"><span data-stu-id="59ee7-154">Services are aligned around business domains.</span></span>
* <span data-ttu-id="59ee7-155">Os serviços se comunicam por meio de APIs leves, normalmente usando HTTP como transporte.</span><span class="sxs-lookup"><span data-stu-id="59ee7-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
* <span data-ttu-id="59ee7-156">Os serviços podem ser implantados e atualizados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="59ee7-156">Services can be deployed and upgraded independently.</span></span>
* <span data-ttu-id="59ee7-157">Os serviços não são dependentes de um único repositório de dados.</span><span class="sxs-lookup"><span data-stu-id="59ee7-157">Services aren't dependent on a single data store.</span></span>
* <span data-ttu-id="59ee7-158">O sistema foi projetado com falha em mente e o aplicativo ainda pode ser executado mesmo quando determinados serviços falham.</span><span class="sxs-lookup"><span data-stu-id="59ee7-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="59ee7-159">Os microserviços não precisam ser mutuamente exclusivos a outras abordagens de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="59ee7-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="59ee7-160">Por exemplo, uma arquitetura de N camadas pode usar microserviços para a camada intermediária.</span><span class="sxs-lookup"><span data-stu-id="59ee7-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="59ee7-161">Também é possível implementar os microserviços de várias maneiras, desde diretórios virtuais em hosts IIS até contêineres.</span><span class="sxs-lookup"><span data-stu-id="59ee7-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="59ee7-162">As características dos microserviços os tornam especialmente ideais para implementações sem servidor.</span><span class="sxs-lookup"><span data-stu-id="59ee7-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Arquitetura de microsserviços](./media/microservices-architecture.png)

<span data-ttu-id="59ee7-164">Os prós de arquiteturas de microserviço incluem:</span><span class="sxs-lookup"><span data-stu-id="59ee7-164">The pros of microservices architectures include:</span></span>

* <span data-ttu-id="59ee7-165">A refatoração geralmente é isolada para um único serviço.</span><span class="sxs-lookup"><span data-stu-id="59ee7-165">Refactoring is often isolated to a single service.</span></span>
* <span data-ttu-id="59ee7-166">Os serviços podem ser atualizados independentemente um do outro.</span><span class="sxs-lookup"><span data-stu-id="59ee7-166">Services can be upgraded independently of each other.</span></span>
* <span data-ttu-id="59ee7-167">Resiliência e elasticidade podem ser ajustadas às demandas de serviços individuais.</span><span class="sxs-lookup"><span data-stu-id="59ee7-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
* <span data-ttu-id="59ee7-168">O desenvolvimento pode ocorrer em paralelo em diferentes equipes e plataformas.</span><span class="sxs-lookup"><span data-stu-id="59ee7-168">Development can happen in parallel across disparate teams and platforms.</span></span>
* <span data-ttu-id="59ee7-169">É mais fácil escrever testes abrangentes para serviços isolados.</span><span class="sxs-lookup"><span data-stu-id="59ee7-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="59ee7-170">Os microserviços vêm com seus próprios desafios, incluindo:</span><span class="sxs-lookup"><span data-stu-id="59ee7-170">Microservices come with their own challenges, including:</span></span>

* <span data-ttu-id="59ee7-171">Determinar quais serviços estão disponíveis e como chamá-los.</span><span class="sxs-lookup"><span data-stu-id="59ee7-171">Determining what services are available and how to call them.</span></span>
* <span data-ttu-id="59ee7-172">Gerenciando o ciclo de vida dos serviços.</span><span class="sxs-lookup"><span data-stu-id="59ee7-172">Managing the lifecycle of services.</span></span>
* <span data-ttu-id="59ee7-173">Entender como os serviços se integram no aplicativo geral.</span><span class="sxs-lookup"><span data-stu-id="59ee7-173">Understanding how services fit together in the overall application.</span></span>
* <span data-ttu-id="59ee7-174">Teste completo do sistema de chamadas feitas em diferentes serviços.</span><span class="sxs-lookup"><span data-stu-id="59ee7-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="59ee7-175">Por fim, há soluções para lidar com todos esses desafios, incluindo o aproveitamento dos benefícios do sem servidor que são discutidos posteriormente.</span><span class="sxs-lookup"><span data-stu-id="59ee7-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="59ee7-176">[Anterior](index.md)
>[Próximo](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="59ee7-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>