---
title: Rechercher le processus ASP.NET en cours d’exécution | Microsoft Docs
ms.date: 11/04/2018
ms.topic: how-to
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
ms.openlocfilehash: c14067d58289dd0b41fa526937a0553c10934ea7
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349605"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Rechercher le nom du processus ASP.NET

Pour déboguer une application en cours d’exécution [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , le débogueur Visual Studio doit s’attacher au [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus par son nom.

**Pour savoir quel processus exécute une application ASP.NET :**

1. Une fois l’application en cours d’exécution, dans Visual Studio, sélectionnez **Déboguer**  >  **attacher au processus**.

1. Dans la boîte de dialogue **attacher au processus** , tapez les premières lettres des noms de processus dans la liste suivante, ou entrez-les dans la zone de recherche. Celui qui est en cours d’exécution est celui qui exécute l’application ASP.NET. Connectez-vous à ce processus pour déboguer l’application.

    - *w3wp.exe* est IIS 6,0 et versions ultérieures.
    - *aspnet_wp.exe* est une version antérieure d’IIS.
    - *iisexpress.exe* est iisexpress.
    - *dotnet.exe* n’est ASP.net core.
    - *inetinfo.exe* sont des applications ASP plus anciennes qui s’exécutent in-process.

>[!NOTE]
>Visual Studio 2012 et [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] le code antérieur peuvent se trouver sur le système de fichiers et s’exécuter sur le serveur de test *WebDev.WebServer.exe* ou *WebDev.WebServer40.exe*. Dans ce cas, pour le débogage local, attachez à *WebDev.WebServer.exe* ou *WebDev.WebServer40.exe* au lieu du [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processus.

**Voir aussi :**

- [Attacher à un processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Conditions préalables pour le débogage distant d’applications Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Configuration système requise](../debugger/aspnet-debugging-system-requirements.md)
- [Déboguer des applications ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)