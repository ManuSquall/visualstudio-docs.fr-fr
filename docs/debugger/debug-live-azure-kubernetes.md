---
title: Déboguer les Services de Kubernetes en direct ASP.NET Azure
description: Découvrez comment définir des points d’ancrage et afficher les captures instantanées avec le débogueur de capture instantanée.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: vs-2019
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 437c9a6d75df3c063a53bda0549c22fd0cbc0876
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627946"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Déboguer les Services Kubernetes Azure live ASP.NET à l’aide du débogueur de capture instantanée

Le débogueur de capture instantanée prend un instantané de vos applications de production lors de l’exécution de code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

Points d’ancrage et points de journalisation sont similaires aux points d’arrêt, mais contrairement aux points d’arrêt, les points d’ancrage n’arrête l’application lorsqu’il est atteint. En règle générale, capturez un instantané à un point d’ancrage prend 10 à 20 millisecondes.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrez le débogueur de capture instantanée
> * Définir un point d’ancrage et afficher un instantané
> * Définir un point de journalisation

## <a name="prerequisites"></a>Prérequis

* Débogueur de captures instantanées pour les Services de Azure Kubernetes est uniquement disponible en version préliminaire de Visual Studio 2019 Enterprise ou une version ultérieure avec le **charge de travail de développement Azure**. (Sous la **composants individuels** onglet, vous retrouver sous **débogage et test** > **débogueur de capture instantanée**.)

    S’il n’est pas déjà installé, installez [Visual Studio 2019 Enterprise preview](https://visualstudio.microsoft.com/vs/preview/).

* Collecte de captures instantanées est disponible pour les applications web de Services de Kubernetes Azure suivantes :
  * Applications ASP.NET Core s’exécutant sur .NET Core 2.2 ou version ultérieure sur Debian 9.
  * Applications ASP.NET Core s’exécutant sur .NET Core 2.2 ou version ultérieure sur 3.8 Alpine.
  * Applications ASP.NET Core s’exécutant sur .NET Core 2.2 ou version ultérieure sur Ubuntu 18.04.

    > [!NOTE]
    > Pour vous aider à activer la prise en charge pour le débogueur de capture instantanée dans ACS, nous avons fourni un [référentiel contenant un ensemble de fichiers Dockerfile qui illustrent l’installation sur les images Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Ouvrez votre projet et démarrer le débogueur de capture instantanée

1. Ouvrez le projet que vous souhaitez le débogage d’instantané.

    > [!IMPORTANT]
    > Débogage d’instantané, vous devez ouvrir le *même version de code source* qui est publié dans votre service Azure Kubernetes.

1. Attacher le débogueur de capture instantanée. Vous pouvez utiliser une des différentes méthodes :

    * Choisissez **Déboguer > attacher le débogueur de capture instantanée...** . Sélectionnez ressources AKS votre application web est déployée sur un compte de stockage Azure, puis cliquez sur **attacher**.

      ![Lancer le débogueur de capture instantanée à partir du menu Débogage](../debugger/media/snapshot-debug-menu-attach.png)

    * Cliquez avec le bouton droit sur votre projet, puis sélectionnez **publier**, puis, dans la page Publier, cliquez sur **attacher un débogueur de capture instantanée**. Sélectionnez ressources AKS votre application web est déployée sur un compte de stockage Azure, puis cliquez sur **attacher**.
    ![Lancer le débogueur de capture instantanée à partir de la page de publication](../debugger/media/snapshot-publish-attach.png)

    * Dans le débogage cibler le menu de liste déroulante, sélectionnez **débogueur de capture instantanée**, positionnement **F5** et si nécessaire sélectionnez ressources AKS votre application web est déployée sur un stockage Azure du compte, puis cliquez sur  **Attacher**.
    ![Lancer le débogueur de capture instantanée à partir du menu de liste déroulante de F5](../debugger/media/snapshot-F5-dropdown-attach.png)

    * À l’aide de l’Explorateur de Cloud (**Affichage > Cloud Explorer**), avec le bouton droit de la ressource AKS votre application web est déployée sur et un compte de stockage Azure, puis cliquez sur **attacher un débogueur de capture instantanée**.

      ![Lancer le débogueur de capture instantanée à partir de l’Explorateur de Cloud](../debugger/media/snapshot-launch.png)

    > [!NOTE]
    > L’extension de site Application Insights prend également en charge le débogage d’instantané. Si vous rencontrez un message d’erreur « extension obsolète de site », consultez [résolution des problèmes de conseils et les problèmes connus pour le débogage d’instantané](../debugger/debug-live-azure-apps-troubleshooting.md) détails de la mise à niveau.

   ![Mode de débogage d’instantané](../debugger/media/snapshot-message.png)

   Le **Modules** fenêtre vous montre que tous les modules ont chargés pour Azure App Service (choisissez **Déboguer > Windows > Modules** pour ouvrir cette fenêtre).

   ![Vérification de la fenêtre Modules](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Définir un point d’ancrage

1. Dans l’éditeur de code, cliquez sur la marge gauche en regard d’une ligne de code qui que vous intéresse définir un point d’ancrage. Assurez-vous que c’est le code que vous connaissez s’exécutera.

   ![Définir un point d’ancrage](../debugger/media/snapshot-set-snappoint.png)

1. Cliquez sur **démarrer la collecte** pour activer le point d’ancrage.

   ![Activer le point d’ancrage](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Vous ne pouvez pas passer lors de l’affichage d’un instantané, mais vous pouvez placer plusieurs points d’ancrage dans votre code pour suivre l’exécution au niveau des lignes différentes de code. Si vous avez plusieurs points d’ancrage dans votre code, le débogueur de capture instantanée permet de s’assurer que les captures instantanées correspondantes sont à partir de la même session de l’utilisateur final. Le débogueur de capture instantanée pour cela, même s’il existe de nombreux utilisateurs atteindre votre application.

## <a name="take-a-snapshot"></a>Prendre un instantané

Lorsqu’un point d’ancrage est allumé, il capture un instantané chaque fois qu’exécute la ligne de code où se trouve le point d’ancrage. Cette exécution peut être dû à une demande réelle sur votre serveur. Pour forcer votre point d’ancrage à atteindre, accédez à la vue du navigateur de votre site web et prendre les mesures nécessaires qui provoquent de votre point d’ancrage à atteindre.

## <a name="inspect-snapshot-data"></a>Inspecter les données d’instantané

1. Lorsque le point d’ancrage est atteint, une capture instantanée apparaît dans la fenêtre Outils de Diagnostic. Pour ouvrir cette fenêtre, choisissez **Déboguer > Windows > Afficher les outils de Diagnostic**.

   ![Ouvrir un point d’ancrage](../debugger/media/snapshot-diagsession-window.png)

1. Double-cliquez sur le point d’ancrage pour ouvrir l’instantané dans l’éditeur de code.

   ![Inspecter les données d’instantané](../debugger/media/snapshot-inspect-data.png)

   Dans cette vue, vous pouvez pointer sur les variables pour afficher les DataTips, utilisez le **variables locales**, **espions**, et **pile des appels** windows et également évaluer des expressions.

    Le site Web lui-même est toujours en direct et les utilisateurs finaux ne sont pas affectées. Une seule capture instantanée est capturée par le point d’ancrage par défaut : une fois une capture instantanée est capturée désactive le point d’ancrage. Si vous souhaitez capturer un autre instantané sur le point d’ancrage, vous pouvez activer le point d’ancrage précédent en cliquant sur **mise à jour Collection**.

Vous pouvez également ajouter plusieurs points d’ancrage à votre application et sous tension avec la **mise à jour Collection** bouton.

**Besoin d’aide ?** Consultez le [dépannage et problèmes connus](../debugger/debug-live-azure-apps-troubleshooting.md) et [Forum aux questions sur le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md) pages.

## <a name="set-a-conditional-snappoint"></a>Définir un point d’ancrage conditionnel

S’il est difficile de recréer un état particulier dans votre application, considérez que l’utilisation d’un point d’ancrage conditionnel peut aider à. Points d’ancrage conditionnel vous aident à que éviter un instantané jusqu'à ce que l’application passe à l’état souhaité, par exemple lorsqu’une variable a une valeur particulière que vous souhaitez inspecter. Vous pouvez définir des conditions à l’aide d’expressions, filtres, ou nombre d’accès.

#### <a name="to-create-a-conditional-snappoint"></a>Pour créer un point d’ancrage conditionnel

1. Cliquez sur une icône de point d’ancrage (la balle creuse) et choisissez **paramètres**.

   ![Choisir des paramètres](../debugger/media/snapshot-snappoint-settings.png)

1. Dans la fenêtre Paramètres de point d’ancrage, tapez une expression.

   ![Tapez une expression](../debugger/media/snapshot-snappoint-conditions.png)

   Dans l’illustration précédente, la capture instantanée est uniquement nécessaire pour le point d’ancrage lorsque `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Définir un point de journalisation

Outre l’extraction d’un instantané lorsqu’un point d’ancrage est atteint, vous pouvez également configurer un point d’ancrage pour consigner un message (autrement dit, créer un point de journalisation). Vous pouvez définir des points de journalisation sans avoir à redéployer votre application. Points de journalisation sont exécutés virtuellement, entraînant des aucun impact ou les effets à votre application en cours d’exécution.

#### <a name="to-create-a-logpoint"></a>Pour créer un point de journalisation

1. Cliquez sur une icône de point d’ancrage (l’Hexagone bleu) et choisissez **paramètres**.

1. Dans la fenêtre Paramètres de point d’ancrage, sélectionnez **Actions**.

    ![Créer un point de journalisation](../debugger/media/snapshot-logpoint.png)

1. Dans le **Message** , vous pouvez saisir le nouveau message de journal vous souhaitez journaliser. Vous pouvez également évaluer des variables dans votre message de journal en les plaçant entre accolades.

    Si vous choisissez **envoyer dans la fenêtre sortie**, lorsque le point de journalisation est atteint, le message s’affiche dans la fenêtre Outils de Diagnostic.

    ![Point de journalisation des données dans la fenêtre diagsession](../debugger/media/snapshot-logpoint-output.png)

    Si vous choisissez **envoyer au journal des applications**, lorsque le point de journalisation est atteint, le message s’affiche de n’importe où que vous pouvez voir des messages à partir de `System.Diagnostics.Trace` (ou `ILogger` dans .NET Core), tel que [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment utiliser le débogueur de capture instantanée pour Azure Kubernetes. Voulez-vous en savoir plus sur cette fonctionnalité.

> [!div class="nextstepaction"]
> [FAQ pour le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)