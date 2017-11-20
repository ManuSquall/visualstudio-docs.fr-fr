---
title: "Quelles sont les nouveautés du débogueur dans Visual Studio 2017 | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: "81"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a08c56ae60822e6d4183e5789c68cbe383b4dd5
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Quelles sont les nouveautés du débogueur dans[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Le débogueur inclut ces nouvelles fonctionnalités :

- Nouveauté de 15.5, le **instantané débogueur** prend un instantané de vos applications de production lors de l’exécution de code qui vous intéressez. Pour indiquer au débogueur de prendre un instantané, vous définissez snappoints et logpoints dans votre code. Le débogueur vous permet de voir exactement ce qui s’est produite, sans affecter le trafic de votre application de production. Le débogueur de l’instantané peut vous aider à réduire considérablement le temps que nécessaire pour résoudre les problèmes qui se produisent dans les environnements de production.

    Collection d’instantané est disponible pour les applications web suivantes en cours d’exécution dans Azure App Service :

    * Les applications ASP.NET exécutées sur .NET Framework 4.6.1 ou version ultérieure.
    * Applications ASP.NET Core en cours d’exécution sur .NET Core 2.0 ou version ultérieure sur Windows.

    Pour plus d’informations, consultez [déboguer des applications ASP.NET en direct à l’aide du débogueur de l’instantané](../debugger/debug-live-azure-applications.md).

- Nouveautés dans Visual Studio Enterprise 15.5 uniquement, **différée IntelliTrace étape** prend automatiquement un instantané de votre application à chaque point d’arrêt et le débogueur événement d’étape. Les instantanés enregistrés permettent de revenir en arrière pour les points d’arrêt précédents ou étapes et afficher l’état de l’application tel qu’il était dans le passé. IntelliTrace d’étape différée peut faire gagner du temps quand vous souhaitez afficher l’état précédent de l’application mais ne souhaitez pas redémarrer le débogage ou de recréer l’état de l’application souhaitée.

    Vous pouvez rechercher et afficher des instantanés à l’aide de la **arrière** et **avant** boutons dans la barre d’outils de débogage. Ces boutons Parcourir les événements qui s’affichent dans le **événements** onglet dans le **outils de Diagnostic** fenêtre.

    ![Étape vers l’arrière et des boutons](../debugger/media/intellitrace-step-back-icons-description.png  "boutons arrière et transférer")

    Pour plus d’informations, consultez la [afficher des instantanés à l’aide d’IntelliTrace étape différée](../debugger/how-to-use-intellitrace-step-back.md) page.

- Le **assistance d’Exception** remplace l’Assistant Exception et apparaît dans une zone de la boîte de dialogue non modale où l’erreur s’est produite. Le **assistance d’Exception** fournit un accès plus rapide pour toutes les exceptions internes, une analyse supplémentaire par le débogueur (si disponible) et un accès immédiat à la **paramètres d’Exception** pour l’exception. L’application d’assistance de l’Exception peuvent également être déplacée à une vue flottante s’il ne bloque pas les quelque chose que vous souhaitez voir.

    Par exemple, un **NullReferenceException** affiche maintenant la variable qui comporte la référence null (informations supplémentaires).

    ![Assistance de l’Exception du débogueur](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Pour plus d’informations, consultez le billet de blog sur l’[utilisation de la nouvelle assistance d’exception dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- Vous pouvez maintenant exécuter à une ligne de code tout en étant suspendu dans le débogueur en sélectionnant le **exécuter ici** icône de flèche verte (vous voyez l’icône tout en pointant sur une ligne de code). Cela élimine le besoin de définir des points d’arrêt temporaires.

    ![Exécution du débogueur. Cliquez ensuite sur](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

- Vous pouvez définir des conditions sur les exceptions dans le **paramètres d’Exception** boîte de dialogue (procéder à l’aide de la **modifier la condition** icône dans la boîte de dialogue Paramètres d’Exception ou à l’aide du menu contextuel sur le exception.) Les conditions actuellement pris en charge incluent les noms de module à inclure ou exclure de l’exception.

    ![Conditions d’une Exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Attacher à la boîte de dialogue inclut une nouvelle fonctionnalité de recherche qui vous permettent de rapidement identifier le processus dont vous avez besoin d’attacher à des processus.

    ![Recherche dans attacher au processus](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch") 

Pour plus d’informations sur ces nouvelles fonctionnalités, consultez le [Notes de publication pour [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)