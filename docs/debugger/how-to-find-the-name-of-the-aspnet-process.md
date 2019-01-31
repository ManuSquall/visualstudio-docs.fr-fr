---
title: Recherchez le processus ASP.NET en cours d’exécution | Microsoft Docs
ms.date: 11/04/2018
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 120b5b6818900b8f177a7358d9ef0cee7bb88482
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992618"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Rechercher le nom du processus ASP.NET

Pour déboguer en cours d’exécution [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] application, le débogueur Visual Studio doit attacher à la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus par nom.

**Pour savoir quel processus est en cours d’exécution d’une application ASP.NET :**

1. Avec l’application en cours d’exécution, dans Visual Studio, sélectionnez **déboguer** > **attacher au processus**. 
   
1. Dans le **attacher au processus** boîte de dialogue, tapez les premières lettres du processus de noms à partir de la liste suivante, ou les entrer dans la zone de recherche. Celui qui est en cours d’exécution est l’exécution de l’application ASP.NET. Attacher à ce processus pour déboguer l’application. 
   
    - *w3wp.exe* est IIS 6.0 et versions ultérieures. 
    - *aspnet_wp.exe* est les versions antérieures d’IIS.
    - *iisexpress.exe* est IISExpress.
    - *dotnet.exe* est ASP.NET Core.
    - *Inetinfo.exe* est anciennes applications ASP exécute in-process. 

>[!NOTE]
>Visual Studio 2012 et versions antérieur [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] code peut être sur le système de fichiers et exécuté sur le serveur de test *WebDev.WebServer.exe* ou *WebDev.WebServer40.exe*. Dans ce cas, pour le débogage local, attacher à *WebDev.WebServer.exe* ou *WebDev.WebServer40.exe* au lieu du [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus. 

**Voir aussi :**

 [Attacher à un processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Conditions préalables pour le débogage distant des applications web](/visualstudio/debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer)   
 [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md)   
 [Déboguer des applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)