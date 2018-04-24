---
title: 'Comment : rechercher le nom du processus ASP.NET | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 899860baf5461eb798341cebf775ccde488915b7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Comment : rechercher le nom du processus ASP.NET
Pour créer un attachement à une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en cours d'exécution, vous devez connaître le nom du processus [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] :  

-   Si vous exécutez ASP.NET Core sur IIS ou IIS, le nom du processus est dotnet.exe.

-   Si vous exécutez ASP.NET sur IIS 6.0 ultérieurement, le nom est w3wp.exe.  
  
-   Si vous exécutez ASP.NET sur une version antérieure d’IIS, le nom est aspnet_wp.exe.

-   Si vous exécutez ASP.NET sur IIS, le nom est iisexpress.exe.
  
Pour les applications créées à l’aide de versions de Visual Studio antérieures à Visual Studio 2012, le [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] code peut résider sur le système de fichiers et s’exécuter sous le serveur de test WebDev.WebServer.exe ou WebDev.WebServer40.exe. Dans ce cas, vous devez attacher à WebDev.WebServer.exe ou WebDev.WebServer40.exe au lieu du [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus. Ce scénario s'applique uniquement au débogage local.
  
Les applications antérieures d'ASP s'exécutent à l'intérieur du processus IIS inetinfo.exe lorsqu'elles s'exécutent in-process.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Pour déterminer la version d'IIS sous laquelle l'application s'exécute  

1.  Assurez-vous que l’application est en cours d’exécution et à partir de Visual Studio, utilisez ensuite la [attacher au processus](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) commande.

2.  Tapez la première lettre d’un nom de processus tels que w3wp.exe pour trouver rapidement les processus dans le **processus disponibles** liste.

    Les processus disponibles dans la liste de cette rubrique indique les versions d’IIS sont disponibles, le processus qui exécute votre application.

    > [!NOTE]
    > À partir de Visual Studio 2017, vous pouvez utiliser la zone de recherche pour rechercher le nom du processus.
  
## <a name="see-also"></a>Voir aussi  
 [Attacher à un processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Conditions requises pour le débogage des Applications Web à distance](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Configuration requise](../debugger/aspnet-debugging-system-requirements.md)   
 [Débogage d’Applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)