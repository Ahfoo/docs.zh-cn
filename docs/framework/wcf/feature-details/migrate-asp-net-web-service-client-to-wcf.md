---
title: "如何：将 ASP.NET Web 服务客户端代码迁移到 Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b93460fd6d331b43b49f10cf78fc8863ca1d8d88
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>如何：将 ASP.NET Web 服务客户端代码迁移到 Windows Communication Foundation
下面的过程说明将 ASP.NET Web 服务客户端代码迁移到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所需遵循的几大步骤。  
  
## <a name="procedure"></a>过程  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>将 ASP.NET Web 服务客户端代码迁移到 WCF  
  
1.  确保客户端具有综合测试集。  
  
2.  使用 Visual Studio 2005 将客户端应用程序升级到 .NET 2.0。 运行测试集。  
  
3.  从客户端项目中删除 ASP.NET 客户端代码。 该代码位于使用 WSDL.exe 工具生成的模块中。  
  
4.  生成[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]客户端代码使用[ServiceModel 元数据实用工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 将该代码添加到客户端项目中并将配置输出合并到客户端的现有配置文件中。  
  
5.  编译该应用程序。 用对新 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 客户端类型的引用替换对先前的 ASP.NET 客户端类型的引用，修复编译错误。  
  
6.  运行测试集。  
  
## <a name="see-also"></a>另请参阅  
 [如何： 将 ASP.NET Web 服务代码迁移到 Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
