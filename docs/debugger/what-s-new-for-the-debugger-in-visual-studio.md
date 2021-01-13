---
title: Nouveautés du débogueur dans Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
description: 'Consultez les nouvelles fonctionnalités du débogueur version 15,5. Les sont les suivants : des instantanés du code sélectionné d’applications en production et de l’étape précédente d’IntelliTrace.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 986ebf20cd49569bfcaf471b9bef994dfe774437
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149402"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Nouveautés du débogueur dans Visual Studio 2017

Le débogueur comprend les nouvelles fonctionnalités suivantes :

- Nouveauté de la version 15,5, le **débogueur de capture instantanée** prend un instantané de vos applications en production lorsque le code qui vous intéresse s’exécute. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

    La fonctionnalité de capture instantanée est disponible pour les applications web suivantes qui s’exécutent dans Azure App Service :

  * Applications ASP.NET exécutées sur .NET Framework version 4.6.1 ou ultérieure.
  * Applications ASP.NET Core exécutées sur .NET Core version 2.0 ou ultérieure sur Windows.

    Pour plus d’informations, consultez [Déboguer des applications ASP.NET en production avec le débogueur de capture instantanée](../debugger/debug-live-azure-applications.md).

- Nouveauté de la version 15,5 uniquement dans Visual Studio Enterprise, **IntelliTrace** effectue automatiquement une capture instantanée de votre application à chaque point d’arrêt et événement d’étape du débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

    Vous pouvez parcourir et afficher les captures instantanées à l’aide des boutons **Étape précédente** et **Étape suivante** situés dans la barre d’outils de débogage. Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**.

    ![Boutons précédent et suivant](../debugger/media/intellitrace-step-back-icons-description.png  "Boutons précédent et suivant")

    Pour plus d’informations, consultez la page [Inspecter les états antérieurs de l’application avec IntelliTrace](view-historical-application-state.md).

- L' **assistance** de l’exception remplace l’Assistant exception et s’affiche dans une boîte de dialogue non modale dans laquelle l’erreur s’est produite. L' **assistance** de l’exception fournit un accès plus rapide à toutes les exceptions internes, une analyse supplémentaire par le débogueur (si disponible) et un accès immédiat aux **paramètres d’exception** pour l’exception. L’assistance de l’exception peut également être déplacée vers une vue flottante si elle bloque une action que vous devez voir.

    Par exemple, une **exception NullReferenceException** affiche maintenant la variable qui a la référence null (informations supplémentaires).

    ![Assistance sur l’exception du débogueur](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Pour plus d’informations, consultez le billet de blog sur l’[utilisation de la nouvelle assistance d’exception dans Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/).

- Vous pouvez maintenant exécuter jusqu’à une ligne de code pendant que vous êtes en pause dans le débogueur en sélectionnant l’icône de flèche verte **exécuter l’exécution jusqu’ici** (l’icône s’affiche lorsque vous pointez sur une ligne de code). Cela élimine la nécessité de définir des points d’arrêt temporaires.

    ![Exécution du débogueur sur](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Vous pouvez définir des conditions sur les exceptions dans la boîte de dialogue **paramètres d’exception** (pour cela, vous pouvez utiliser l’icône **modifier la condition** dans la boîte de dialogue Paramètres d’exception ou en utilisant le menu contextuel sur l’exception). Les conditions actuellement prises en charge incluent les noms de modules à inclure ou exclure pour l’exception.

    ![Conditions sur une exception](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- La boîte de dialogue Attacher au processus comprend une nouvelle fonctionnalité de recherche qui peut vous aider à identifier plus rapidement le processus auquel vous devez attacher.

    ![Rechercher dans attacher au processus](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Pour plus d’informations sur ces nouvelles fonctionnalités, consultez les [notes de [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] publication de ](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)