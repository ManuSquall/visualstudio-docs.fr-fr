---
title: Quelles sont les nouveautés du débogueur dans Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
ms.date: 01/22/2018
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9c6f2eb4be56be8cf5e25c3238a91819df3bc574
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901380"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Nouveautés du débogueur dans Visual Studio 2017

Le débogueur inclut ces nouvelles fonctionnalités :

- Nouveautés de la version 15.5, le **débogueur de capture instantanée** prend un instantané de vos applications de production lors de l’exécution de code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

    La fonctionnalité de capture instantanée est disponible pour les applications web suivantes qui s’exécutent dans Azure App Service :

  * Applications ASP.NET exécutées sur .NET Framework version 4.6.1 ou ultérieure.
  * Applications ASP.NET Core exécutées sur .NET Core version 2.0 ou ultérieure sur Windows.

    Pour plus d’informations, consultez [Déboguer des applications ASP.NET en production avec le débogueur de capture instantanée](../debugger/debug-live-azure-applications.md).

- Nouveautés de la version 15.5 uniquement, dans Visual Studio Enterprise **en arrière IntelliTrace** prend automatiquement un instantané de votre application à chaque point d’arrêt et le débogueur événement d’étape. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

    Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

    ![Boutons Étape précédente et Étape suivante](../debugger/media/intellitrace-step-back-icons-description.png  "Boutons Étape précédente et Étape suivante")

    Pour plus d’informations, consultez la page [Inspecter les états antérieurs de l’application avec IntelliTrace](../debugger/view-historical-application-state.md).

- Le **assistance d’Exception** remplace l’Assistant Exception et apparaît dans une zone de la boîte de dialogue non modale où l’erreur s’est produite. Le **assistance d’Exception** fournit un accès plus rapide pour les exceptions internes, une analyse supplémentaire par le débogueur (si disponible) et un accès immédiat à la **paramètres d’Exception** pour l’exception. L’assistance d’Exception peuvent également être déplacée vers une vue flottante si il ne bloque pas quelque chose que vous devez voir.

    Par exemple, un **NullReferenceException** affiche maintenant la variable dont la référence null (informations supplémentaires).

    ![Assistance de l’Exception du débogueur](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Pour plus d’informations, consultez le billet de blog sur l’[utilisation de la nouvelle assistance d’exception dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

- Vous pouvez maintenant exécuter à une ligne de code tout en étant suspendu dans le débogueur en sélectionnant le **exécuter l’exécution jusqu’ici** icône de flèche verte (vous voyez l’icône tout en pointant sur une ligne de code). Cela vous évite de devoir définir des points d’arrêt temporaires.

    ![Débogueur de l’exécuter jusqu’au clic](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Vous pouvez définir des conditions sur les exceptions dans le **paramètres d’Exception** boîte de dialogue (vous pouvez le faire à l’aide de la **modifier la condition** icône dans la boîte de dialogue Paramètres d’Exception ou en utilisant le menu contextuel sur le exception.) Conditions actuellement pris en charge incluent les noms de module à inclure ou exclure de l’exception.

    ![Conditions d’une Exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Attacher à la boîte de dialogue inclut une nouvelle fonctionnalité de recherche qui peut vous aider à plus rapidement identifier le processus dont vous avez besoin d’attacher à des processus.

    ![Recherche dans attacher au processus](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Pour plus d’informations sur ces nouvelles fonctionnalités, consultez le [Notes de publication pour [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)