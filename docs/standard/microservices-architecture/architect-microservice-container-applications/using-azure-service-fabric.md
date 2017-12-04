---
title: "使用 Azure Service Fabric"
description: "为容器化的.NET 应用程序的.NET 微服务体系结构 |使用 Azure Service Fabric"
keywords: "Docker, 微服务, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa15f9cf9bc60e9e70607da921f2ce2c75e39ec2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2017
---
# <a name="using-azure-service-fabric"></a><span data-ttu-id="f98e1-104">使用 Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f98e1-104">Using Azure Service Fabric</span></span>

<span data-ttu-id="f98e1-105">Azure Service Fabric 产生从将框产品不同，后者是通常整体样式，传送到提供服务的 Microsoft 的转换。</span><span class="sxs-lookup"><span data-stu-id="f98e1-105">Azure Service Fabric arose from Microsoft’s transition from delivering box products, which were typically monolithic in style, to delivering services.</span></span> <span data-ttu-id="f98e1-106">构建并运行大型大规模情况下，如 Azure SQL 数据库、 Azure Cosmos DB、 Azure Service Bus 或 Cortana 的后端服务的体验调整 Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="f98e1-106">The experience of building and operating large services at scale, such as Azure SQL Database, Azure Cosmos DB, Azure Service Bus, or Cortana’s Backend, shaped Service Fabric.</span></span> <span data-ttu-id="f98e1-107">随着越来越多的服务采用它，通过逐步发展平台。</span><span class="sxs-lookup"><span data-stu-id="f98e1-107">The platform evolved over time as more and more services adopted it.</span></span> <span data-ttu-id="f98e1-108">重要的是，Service Fabric 必须在运行不仅在 Azure 中，还在独立 Windows 服务器部署。</span><span class="sxs-lookup"><span data-stu-id="f98e1-108">Importantly, Service Fabric had to run not only in Azure but also in standalone Windows Server deployments.</span></span>

<span data-ttu-id="f98e1-109">Service Fabric 的目的是为了解决难题的生成和运行服务并有效地，利用基础结构资源，以便团队可以解决业务问题使用微服务方法。</span><span class="sxs-lookup"><span data-stu-id="f98e1-109">The aim of Service Fabric is to solve the hard problems of building and running a service and utilizing infrastructure resources efficiently, so that teams can solve business problems using a microservices approach.</span></span>

<span data-ttu-id="f98e1-110">Service Fabric 提供了两个广泛的区域，可帮助你构建的应用程序使用微服务方法：</span><span class="sxs-lookup"><span data-stu-id="f98e1-110">Service Fabric provides two broad areas to help you build applications that use a microservices approach:</span></span>

-   <span data-ttu-id="f98e1-111">提供用于部署、 缩放、 升级、 检测，并重新启动失败的服务，发现服务位置、 管理状态，和监视运行状况的系统服务的平台。</span><span class="sxs-lookup"><span data-stu-id="f98e1-111">A platform that provides system services to deploy, scale, upgrade, detect, and restart failed services, discover service location, manage state, and monitor health.</span></span> <span data-ttu-id="f98e1-112">实际上，这些系统服务启用的许多微服务前面所述的特性。</span><span class="sxs-lookup"><span data-stu-id="f98e1-112">These system services in effect enable many of the characteristics of microservices described previously.</span></span>

-   <span data-ttu-id="f98e1-113">编程 Api 或框架，可帮助你构建微服务的应用程序： [reliable actors 和 reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。</span><span class="sxs-lookup"><span data-stu-id="f98e1-113">Programming APIs, or frameworks, to help you build applications as microservices: [reliable actors and reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework).</span></span> <span data-ttu-id="f98e1-114">当然，你可以选择任何代码，以创建你的 microservice，这些 Api 使您的工作更简单，但他们与平台级别更深入地集成。</span><span class="sxs-lookup"><span data-stu-id="f98e1-114">Of course, you can choose any code to build your microservice, but these APIs make the job more straightforward, and they integrate with the platform at a deeper level.</span></span> <span data-ttu-id="f98e1-115">这样就可以运行状况和诊断信息，也可以利用可靠状态管理。</span><span class="sxs-lookup"><span data-stu-id="f98e1-115">This way you can get health and diagnostics information, or you can take advantage of reliable state management.</span></span>

<span data-ttu-id="f98e1-116">Service Fabric 是不可知方面如何生成你的服务，并且可以使用任何技术。</span><span class="sxs-lookup"><span data-stu-id="f98e1-116">Service Fabric is agnostic with respect to how you build your service, and you can use any technology.</span></span> <span data-ttu-id="f98e1-117">但是，它提供内置的编程 Api，使其更轻松地生成微服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-117">However, it provides built-in programming APIs that make it easier to build microservices.</span></span>

<span data-ttu-id="f98e1-118">如所示在图 4-26 日，你可以创建和运行在 Service Fabric 微服务，作为简单的流程或 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="f98e1-118">As shown in Figure 4-26, you can create and run microservices in Service Fabric either as simple processes or as Docker containers.</span></span> <span data-ttu-id="f98e1-119">还有可能混合使用与过程基于同一 Service Fabric 群集中的微服务容器基于微服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-119">It is also possible to mix container-based microservices with process-based microservices within the same Service Fabric cluster.</span></span>

![](./media/image30.png)

<span data-ttu-id="f98e1-120">**图 4-26**。</span><span class="sxs-lookup"><span data-stu-id="f98e1-120">**Figure 4-26**.</span></span> <span data-ttu-id="f98e1-121">部署微服务作为流程或 Azure Service Fabric 中的容器</span><span class="sxs-lookup"><span data-stu-id="f98e1-121">Deploying microservices as processes or as containers in Azure Service Fabric</span></span>

<span data-ttu-id="f98e1-122">基于 Linux 和 Windows 的主机上的 Service Fabric 群集可以分别运行 Docker Linux 容器和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="f98e1-122">Service Fabric clusters based on Linux and Windows hosts can run Docker Linux containers and Windows Containers, respectively.</span></span>

<span data-ttu-id="f98e1-123">有关 Azure Service Fabric 中的容器支持的最新信息，请参阅[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。</span><span class="sxs-lookup"><span data-stu-id="f98e1-123">For up-to-date information about containers support in Azure Service Fabric, see [Service Fabric and containers](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).</span></span>

<span data-ttu-id="f98e1-124">Service Fabric 是一个平台，一个好例子，你可以在其中定义另一个逻辑体系结构 （业务微服务或绑定上下文） 中引入的物理实现比[而不是物理的逻辑体系结构体系结构](#logical-architecture-versus-physical-architecture)部分。</span><span class="sxs-lookup"><span data-stu-id="f98e1-124">Service Fabric is a good example of a platform where you can define a different logical architecture (business microservices or Bounded Contexts) than the physical implementation that were introduced in the [Logical architecture versus physical architecture](#logical-architecture-versus-physical-architecture) section.</span></span> <span data-ttu-id="f98e1-125">例如，如果你实现[有状态 Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)中[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)，其中的部分中引入[与有状态微服务 Stateless](#stateless-versus-stateful-microservices)更高版本，你可以具有与多个物理服务业务微服务概念。</span><span class="sxs-lookup"><span data-stu-id="f98e1-125">For example, if you implement [Stateful Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) in [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), which are introduced in the section [Stateless versus stateful microservices](#stateless-versus-stateful-microservices) later, you can have a business microservice concept with multiple physical services.</span></span>

<span data-ttu-id="f98e1-126">如图 4-27 和从逻辑/业务 microservice 角度看，在实现 Service Fabric 有状态 Reliable Service 时的考虑中所示，你通常需要实现两个级别的服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-126">As shown in Figure 4-27, and thinking from a logical/business microservice perspective, when implementing a Service Fabric Stateful Reliable Service, you usually will need to implement two tiers of services.</span></span> <span data-ttu-id="f98e1-127">第一个是后端有状态 reliable service，用于处理 （每个分区是一个有状态服务） 的多个分区。</span><span class="sxs-lookup"><span data-stu-id="f98e1-127">The first is the back-end stateful reliable service, which handles multiple partitions (each partition is a stateful service).</span></span> <span data-ttu-id="f98e1-128">第二个是指前端服务或网关服务，负责跨多个分区或有状态服务实例的路由和数据聚合。</span><span class="sxs-lookup"><span data-stu-id="f98e1-128">The second is the front-end service, or Gateway service, in charge of routing and data aggregation across multiple partitions or stateful service instances.</span></span> <span data-ttu-id="f98e1-129">该网关服务还使用重试循环访问后端服务可以处理客户端通信。</span><span class="sxs-lookup"><span data-stu-id="f98e1-129">That Gateway service also handles client-side communication with retry loops accessing the backend service.</span></span>
<span data-ttu-id="f98e1-130">如果实现自定义服务或你也可以使用全新的 Service Fabric 的 alternatevely，称为网关服务[反向代理服务](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)。</span><span class="sxs-lookup"><span data-stu-id="f98e1-130">It is called a Gateway service if you implement your custom service, or alternatevely you can also use the out-of-the-box Service Fabric [Reverse Proxy service](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).</span></span>

![](./media/image31.png)

<span data-ttu-id="f98e1-131">**图 4-27**。</span><span class="sxs-lookup"><span data-stu-id="f98e1-131">**Figure 4-27**.</span></span> <span data-ttu-id="f98e1-132">与几个有状态服务实例和自定义网关前端的业务微服务</span><span class="sxs-lookup"><span data-stu-id="f98e1-132">Business microservice with several stateful service instances and a custom gateway front-end</span></span>

<span data-ttu-id="f98e1-133">在任何情况下，当你使用 Service Fabric 有状态 Reliable Services 时，还必须由通常多个物理服务组成的逻辑或业务 microservice （界定上下文）。</span><span class="sxs-lookup"><span data-stu-id="f98e1-133">In any case, when you use Service Fabric Stateful Reliable Services, you also have a logical or business microservice (Bounded Context) that is usually composed of multiple physical services.</span></span> <span data-ttu-id="f98e1-134">每个它们、 网关服务和分区服务无法作为 ASP.NET Web API 服务，在图 4-26 中所示实现。</span><span class="sxs-lookup"><span data-stu-id="f98e1-134">Each of them, the Gateway service and Partition service could be implemented as ASP.NET Web API services, as shown in Figure 4-26.</span></span>

<span data-ttu-id="f98e1-135">可在 Service Fabric 中，组和部署的服务作为组[Service Fabric 应用程序](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)，即打包和部署 orchestrator 或群集的单位。</span><span class="sxs-lookup"><span data-stu-id="f98e1-135">In Service Fabric, you can group and deploy groups of services as a [Service Fabric Application](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), which is the unit of packaging and deployment for the orchestrator or cluster.</span></span> <span data-ttu-id="f98e1-136">因此，Service Fabric 应用程序可以映射到此自治业务和逻辑 microservice 边界或绑定上下文中，同样，以便可以自主部署这些服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-136">Therefore, the Service Fabric Application could be mapped to this autonomous business and logical microservice boundary or Bounded Context, as well, so you could deploy these services autonomously.</span></span>

## <a name="service-fabric-and-containers"></a><span data-ttu-id="f98e1-137">Service Fabric 和容器</span><span class="sxs-lookup"><span data-stu-id="f98e1-137">Service Fabric and containers</span></span>

<span data-ttu-id="f98e1-138">关于在 Service Fabric 中的容器，也可以部署在 Service Fabric 群集中的容器映像中的服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-138">With regard to containers in Service Fabric, you can also deploy services in container images within a Service Fabric cluster.</span></span> <span data-ttu-id="f98e1-139">如图 4-28 所示，大多数情况下将仅有一个容器，每个服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-139">As Figure 4-28 shows, most of the time there will only be one container per service.</span></span>

![](./media/image32.png)

<span data-ttu-id="f98e1-140">**图 4-28**。</span><span class="sxs-lookup"><span data-stu-id="f98e1-140">**Figure 4-28**.</span></span> <span data-ttu-id="f98e1-141">业务微服务与 Service Fabric 中的多个服务 （容器）</span><span class="sxs-lookup"><span data-stu-id="f98e1-141">Business microservice with several services (containers) in Service Fabric</span></span>

<span data-ttu-id="f98e1-142">但是，所谓的"实现 sidecar"容器 （必须在作为逻辑服务的一部分一起部署的两个容器） 也是 Service Fabric 中可能的。</span><span class="sxs-lookup"><span data-stu-id="f98e1-142">However, so-called “sidecar” containers (two containers that must be deployed together as part of a logical service) are also possible in Service Fabric.</span></span> <span data-ttu-id="f98e1-143">重要的是业务微服务是在多个凝聚力元素周围的逻辑边界。</span><span class="sxs-lookup"><span data-stu-id="f98e1-143">The important thing is that a business microservice is the logical boundary around several cohesive elements.</span></span> <span data-ttu-id="f98e1-144">在许多情况下，它可能是单个服务具有单个数据模型，但在某些其他情况下，你可能必须物理多个服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-144">In many cases, it might be a single service with a single data model, but in some other cases you might have physical several services as well.</span></span>

<span data-ttu-id="f98e1-145">截至中旬 2017年在 Service Fabric 中不能将部署在容器上 SF 可靠有状态服务-你可以仅部署无状态服务和容器中的参与者服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-145">As of mid-2017, in Service Fabric you cannot deploy SF Reliable Stateful Services on containers—you can only deploy stateless services and actor services in containers.</span></span> <span data-ttu-id="f98e1-146">但请注意，可以混合在同一 Service Fabric 应用程序的容器中进程中的服务和服务在图 4-29 中所示。</span><span class="sxs-lookup"><span data-stu-id="f98e1-146">But note that you can mix services in processes and services in containers in the same Service Fabric application, as shown in Figure 4-29.</span></span>

![](./media/image33.png)

<span data-ttu-id="f98e1-147">**图 4-29 个**。</span><span class="sxs-lookup"><span data-stu-id="f98e1-147">**Figure 4-29**.</span></span> <span data-ttu-id="f98e1-148">映射到具有容器和有状态服务的 Service Fabric 应用程序的业务微服务</span><span class="sxs-lookup"><span data-stu-id="f98e1-148">Business microservice mapped to a Service Fabric application with containers and stateful services</span></span>

<span data-ttu-id="f98e1-149">有关 Azure Service Fabric 中的容器支持的详细信息，请参阅[Service Fabric 和容器](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)。</span><span class="sxs-lookup"><span data-stu-id="f98e1-149">For more information about container support in Azure Service Fabric, see [Service Fabric and containers](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).</span></span>

## <a name="stateless-versus-stateful-microservices"></a><span data-ttu-id="f98e1-150">与有状态微服务无状态</span><span class="sxs-lookup"><span data-stu-id="f98e1-150">Stateless versus stateful microservices</span></span>

<span data-ttu-id="f98e1-151">如前所述，每个微服务 （逻辑绑定上下文） 必须拥有其域模型 （数据和逻辑）。</span><span class="sxs-lookup"><span data-stu-id="f98e1-151">As mentioned earlier, each microservice (logical Bounded Context) must own its domain model (data and logic).</span></span> <span data-ttu-id="f98e1-152">对于无状态微服务，数据库就会外部，采用类似于 SQL Server 的关系选项或 NoSQL 选项，如 MongoDB 或 Azure Cosmos DB。</span><span class="sxs-lookup"><span data-stu-id="f98e1-152">In the case of stateless microservices, the databases will be external, employing relational options like SQL Server, or NoSQL options like MongoDB or Azure Cosmos DB.</span></span>

<span data-ttu-id="f98e1-153">但服务本身也可以是有状态 Service Fabric 中，这意味着数据位于内微服务中。</span><span class="sxs-lookup"><span data-stu-id="f98e1-153">But the services themselves can also be stateful in Service Fabric, which means that the data resides within the microservice.</span></span> <span data-ttu-id="f98e1-154">此数据可能存在不只是在同一服务器上，但在微服务过程中，在内存中和在硬盘驱动器上保留和复制到其他节点。</span><span class="sxs-lookup"><span data-stu-id="f98e1-154">This data might exist not just on the same server, but within the microservice process, in memory and persisted on hard drives and replicated to other nodes.</span></span> <span data-ttu-id="f98e1-155">图 4-30 显示不同的方法。</span><span class="sxs-lookup"><span data-stu-id="f98e1-155">Figure 4-30 shows the different approaches.</span></span>

![](./media/image34.png)

<span data-ttu-id="f98e1-156">**图 4-30**。</span><span class="sxs-lookup"><span data-stu-id="f98e1-156">**Figure 4-30**.</span></span> <span data-ttu-id="f98e1-157">与有状态微服务无状态</span><span class="sxs-lookup"><span data-stu-id="f98e1-157">Stateless versus stateful microservices</span></span>

<span data-ttu-id="f98e1-158">无状态的方法完全有效，且可以更轻松地实现都比有状态微服务，因为这种方法是类似于传统和已知模式。</span><span class="sxs-lookup"><span data-stu-id="f98e1-158">A stateless approach is perfectly valid and is easier to implement than stateful microservices, since the approach is similar to traditional and well-known patterns.</span></span> <span data-ttu-id="f98e1-159">但无状态微服务施加的进程和数据源之间的延迟。</span><span class="sxs-lookup"><span data-stu-id="f98e1-159">But stateless microservices impose latency between the process and data sources.</span></span> <span data-ttu-id="f98e1-160">当你尝试通过其他缓存和队列提高性能时，它们还会涉及更移动片段。</span><span class="sxs-lookup"><span data-stu-id="f98e1-160">They also involve more moving pieces when you are trying to improve performance with additional cache and queues.</span></span> <span data-ttu-id="f98e1-161">结果是，你可以得到复杂的体系结构具有太多层。</span><span class="sxs-lookup"><span data-stu-id="f98e1-161">The result is that you can end up with complex architectures that have too many tiers.</span></span>

<span data-ttu-id="f98e1-162">与此相反，[有状态微服务](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)可以在高级方案中，excel，因为没有在域逻辑和数据之间的滞后时间。</span><span class="sxs-lookup"><span data-stu-id="f98e1-162">In contrast, [stateful microservices](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) can excel in advanced scenarios, because there is no latency between the domain logic and data.</span></span> <span data-ttu-id="f98e1-163">大量的数据处理，返回游戏结束，数据库作为一种服务，并受益于有状态服务，启用更快的访问权限的本地状态的所有其他低延迟方案。</span><span class="sxs-lookup"><span data-stu-id="f98e1-163">Heavy data processing, gaming back ends, databases as a service, and other low-latency scenarios all benefit from stateful services, which enable local state for faster access.</span></span>

<span data-ttu-id="f98e1-164">无状态和有状态服务是补充。</span><span class="sxs-lookup"><span data-stu-id="f98e1-164">Stateless and stateful services are complementary.</span></span> <span data-ttu-id="f98e1-165">例如，你可以在正确的图中，有状态服务，无法拆分为多个分区看到图 4-30。</span><span class="sxs-lookup"><span data-stu-id="f98e1-165">For instance, you can see in Figure 4-30, in the right diagram, that a stateful service could be split into multiple partitions.</span></span> <span data-ttu-id="f98e1-166">若要访问这些分区，可能需要充当一个知道如何解决每个分区基于分区键的网关服务的无状态服务。</span><span class="sxs-lookup"><span data-stu-id="f98e1-166">To access those partitions, you might need a stateless service acting as a gateway service that knows how to address each partition based on partition keys.</span></span>

<span data-ttu-id="f98e1-167">有状态服务有缺点。</span><span class="sxs-lookup"><span data-stu-id="f98e1-167">Stateful services do have drawbacks.</span></span> <span data-ttu-id="f98e1-168">施加的横向扩展允许的复杂性。跨有状态微服务和分区的数据，通常会由外部数据库系统实现的功能必须解决的任务，例如数据复制。</span><span class="sxs-lookup"><span data-stu-id="f98e1-168">They impose a level of complexity that allows to scale out. Functionality that would usually be implemented by external database systems must be addressed for tasks such as data replication across stateful microservices and data partitioning.</span></span> <span data-ttu-id="f98e1-169">但是，这是一个其中 orchestrator 喜欢方面[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)与其[有状态 reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)有助于最大 — 通过简化开发和有状态的生命周期微服务使用[Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)和[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)。</span><span class="sxs-lookup"><span data-stu-id="f98e1-169">However, this is one of the areas where an orchestrator like [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) with its [stateful reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) can help the most—by simplifying the development and lifecycle of stateful microservices using the [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) and [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span></span>

<span data-ttu-id="f98e1-170">允许有状态服务，支持 Actor 模式，并可提高程度的容错和业务逻辑和数据之间的延迟其他微服务框架是 Microsoft[奥尔良](https://github.com/dotnet/orleans)，请从 Microsoft Research [Akka.NET](http://getakka.net/)。</span><span class="sxs-lookup"><span data-stu-id="f98e1-170">Other microservice frameworks that allow stateful services, that support the Actor pattern, and that improve fault tolerance and latency between business logic and data are Microsoft [Orleans](https://github.com/dotnet/orleans), from Microsoft Research, and [Akka.NET](http://getakka.net/).</span></span> <span data-ttu-id="f98e1-171">这两种框架当前改善它们对 Docker 的支持。</span><span class="sxs-lookup"><span data-stu-id="f98e1-171">Both frameworks are currently improving their support for Docker.</span></span>

<span data-ttu-id="f98e1-172">请注意，Docker 容器本身无状态。</span><span class="sxs-lookup"><span data-stu-id="f98e1-172">Note that Docker containers are themselves stateless.</span></span> <span data-ttu-id="f98e1-173">如果你想要实现一个有状态服务，你需要一个前文所述的其他说明性和较高级别的框架。</span><span class="sxs-lookup"><span data-stu-id="f98e1-173">If you want to implement a stateful service, you need one of the additional prescriptive and higher-level frameworks noted earlier.</span></span> 

>[!div class="step-by-step"]
<span data-ttu-id="f98e1-174">[以前](scalable-available-multi-container-microservice-applications.md) [下一步] (.../docker-application-development-process/index.md)</span><span class="sxs-lookup"><span data-stu-id="f98e1-174">[Previous] (scalable-available-multi-container-microservice-applications.md) [Next] (../docker-application-development-process/index.md)</span></span>