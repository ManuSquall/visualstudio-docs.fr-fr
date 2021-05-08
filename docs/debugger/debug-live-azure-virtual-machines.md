---
title: Déboguer des machines virtuelles Azure ASP.NET et des groupes identiques
description: Découvrez comment utiliser la Débogueur de capture instantanée dans Visual Studio pour définir points d’ancrage et prendre des instantanés pendant le débogage d’applications ASP.NET en direct sur des machines virtuelles Azure et des groupes identiques.
ms.custom: SEO-VS-2020
ms.date: 02/06/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: bdab6b3f559628506dd301d6ced449f1e69152a6
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798490"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Déboguer des applications ASP.NET en production sur des machines virtuelles Azure et des groupes de machines virtuelles identiques Azure à l’aide du Débogueur de capture instantanée

Le Débogueur de capture instantanée prend une capture instantanée de vos applications en production au moment de l’exécution du code qui vous intéresse. Pour indiquer au débogueur de prendre une capture instantanée, vous définissez des points d’ancrage et des points de journalisation dans votre code. Dans le débogueur, vous pouvez voir précisément à quel endroit le code ne s’est pas exécuté correctement, sans que cela impacte le trafic de votre application en production. Snapshot Debugger peut vous aider à résoudre beaucoup plus vite les problèmes rencontrés dans les environnements de production.

Les snappoints et les logpoints sont similaires aux points d’arrêt, mais contrairement à ceux-ci, les snappoints n’arrêtent pas l’application lorsqu’ils sont atteints. En règle générale, la capture d’un instantané sur un snappoint prend entre 10 et 20 millisecondes.

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
> * lancer le Débogueur de capture instantanée ;
> * Définir un snappoint et afficher un instantané
> * Définir un logpoint

## <a name="prerequisites"></a>Prérequis

* Les Débogueur de capture instantanée pour les machines virtuelles Azure et Azure Virtual Machine Scale Sets sont uniquement disponibles pour Visual Studio 2019 Enterprise ou une version ultérieure avec la **charge de travail de développement Azure**. (Dans l’onglet **Composants individuels**, vous le trouverez sous **Débogage et test** > **Débogueur de capture instantanée**.)

    S’il n’est pas déjà installé, installez [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* La collecte d’instantanés est disponible pour les applications Web des groupes de machines virtuelles identiques Azure Machines\Virtual suivants :
  * Applications ASP.NET exécutées sur .NET Framework version 4.6.1 ou ultérieure.
  * Applications ASP.NET Core exécutées sur .NET Core version 2.0 ou ultérieure sur Windows.

  > [!NOTE]
  >  Visual Studio Enterprise s’exécutant sur Windows 32 bits ne sera pas en mesure d’afficher les instantanés.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Ouvrir votre projet et démarrer le Débogueur de capture instantanée

1. Ouvrez le projet pour lequel vous souhaitez exécuter le débogage d’instantané.

    > [!IMPORTANT]
    > Pour déboguer un instantané, vous devez ouvrir la *même version du code source* qui est publiée sur votre service de groupe de machines virtuelles identiques Azure Machine\Virtual.

1. Choisissez **Déboguer > attacher débogueur de capture instantanée...**. Sélectionnez le jeu de mise à l’échelle de machine virtuelle Azure Machine\Virtual sur lequel votre application Web est déployée et un compte de stockage Azure, puis cliquez sur **attacher**. Débogueur de capture instantanée prend également en charge le [service Azure Kubernetes](debug-live-azure-kubernetes.md) et [Azure App service](debug-live-azure-applications.md).

    ![Lancer le Débogueur de capture instantanée à partir du menu Déboguer](../debugger/media/snapshot-debug-menu-attach.png)

    ![Sélectionner une ressource Azure](../debugger/media/snapshot-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La première fois que vous sélectionnez **Joindre le Débogueur de capture instantanée** pour votre machine virtuelle, IIS est redémarré automatiquement.
    > La première fois que vous sélectionnez **attacher débogueur de capture instantanée** pour votre Virtual Machine Scale sets, requiert la mise à niveau manuelle de chaque instance du Virtual Machine Scale sets.

    > [!NOTE]
    > (Visual Studio 2019 version 16,2 et versions ultérieures) Débogueur de capture instantanée a activé le support Cloud Azure. Assurez-vous que la ressource Azure et le compte de stockage Azure que vous sélectionnez proviennent du même Cloud. Si vous avez des questions sur les configurations de [conformité Azure](https://azure.microsoft.com/overview/trusted-cloud/) de votre entreprise, contactez votre administrateur Azure.

    Les métadonnées des **modules** ne sont pas activées pour la première fois, vous accédez à l’application Web et le bouton **Démarrer la collection** devient actif. Visual Studio est maintenant en mode Débogage de capture instantanée.

    ![Mode Débogage de capture instantanée](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Pour VMSS, l’utilisateur doit mettre à niveau manuellement les instances dans leur Virtual Machine Scale Sets après avoir attaché le Débogueur de capture instantanée pour la première fois.

    La fenêtre **modules** affiche une fois que tous les modules ont été chargés pour le groupe de machines virtuelles identiques Azure Machine\Virtual (choisissez **déboguer > modules Windows >** pour ouvrir cette fenêtre).

    ![Fenêtre Vérifier les modules](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Définir un snappoint

1. Dans l’éditeur de code, cliquez sur la marge gauche en regard d’une ligne de code qui vous intéresse pour définir un point d’ancrage. Assurez-vous que le code que vous savez s’exécutera.

    ![Définir un snappoint](../debugger/media/snapshot-set-snappoint.png)

1. Cliquez sur **Lancer la collecte** pour activer le snappoint.

    ![Activer le snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > L’exécution pas à pas n’est pas possible à l’affichage d’une capture instantanée, mais vous pouvez placer plusieurs snappoints dans votre code pour suivre l’exécution sur différentes lignes de code. Si le code comporte plusieurs snappoints, le Débogueur de capture instantanée s’assure que les captures instantanées correspondantes proviennent de la même session d’utilisateur final, même si de nombreux utilisateurs accèdent à l’application.

## <a name="take-a-snapshot"></a>Prendre un instantané

Une fois qu’un point d’ancrage est défini, vous pouvez soit générer manuellement un instantané en accédant à la vue du navigateur de votre site Web et en exécutant la ligne de code marquée, soit en attendant que vos utilisateurs en génèrent un à partir de leur utilisation du site.

## <a name="inspect-snapshot-data"></a>Inspecter les données de capture instantanée

1. Lorsque le snappoint est atteint, une capture instantanée apparaît dans la fenêtre Outils de diagnostic. Pour ouvrir cette fenêtre, choisissez **Déboguer > Fenêtres > Afficher les Outils de diagnostic**.

    ![Ouvrir un snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Double-cliquez sur le snappoint pour ouvrir la capture instantanée dans l’éditeur de code.

    ![Inspecter les données de capture instantanée](../debugger/media/snapshot-inspect-data.png)

    Dans cette vue, vous pouvez pointer sur les variables pour afficher les DataTips, utiliser les fenêtres **Variables locales**, **Suivi**, et **Pile des appels** et évaluer des expressions.

    Le site Web lui-même est toujours actif et les utilisateurs finaux ne sont pas affectés. Par défaut, le snappoint ne prend qu’une capture instantanée : dès que c’est fait, il se désactive. Si vous souhaitez prendre une autre capture instantanée sur le snappoint, vous pouvez le réactiver en cliquant sur **Mettre à jour la collecte**.

Vous pouvez également ajouter d’autres snappoints à votre application et les activer avec le bouton **Mettre à jour la collecte**.

**Besoin d’aide ?** Voir les pages [Résolution des problèmes et problèmes connus](../debugger/debug-live-azure-apps-troubleshooting.md) et [FAQ du débogage de captures instantanées](../debugger/debug-live-azure-apps-faq.yml).

## <a name="set-a-conditional-snappoint"></a>Définir un snappoint conditionnel

S’il est difficile de recréer un état particulier dans votre application, envisagez d’utiliser un point d’ancrage conditionnel. Les points d’ancrage conditionnelles vous permettent de contrôler le moment où un instantané doit être utilisé, par exemple lorsqu’une variable contient une valeur particulière que vous souhaitez inspecter. Les conditions sont définies à l’aide d’expressions, de filtres ou d’un nombre d’accès.

#### <a name="to-create-a-conditional-snappoint"></a>Créer un snappoint conditionnel

1. Cliquez avec le bouton droit sur une icône de snappoint (sphère) et choisissez **Paramètres**.

   ![Choisir des paramètres](../debugger/media/snapshot-snappoint-settings.png)

1. Dans la fenêtre des paramètres du snappoint, tapez une expression.

   ![Taper une expression](../debugger/media/snapshot-snappoint-conditions.png)

   Dans l’illustration précédente, la capture instantanée n’est prise pour le snappoint que si `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Définir un logpoint

Nous avons vu comment prendre une capture instantanée lorsqu’un snappoint est atteint. Il est également possible de configurer un snappoint de sorte qu’il consigne un message (autrement dit, qu’il crée un logpoint). Il n’est pas nécessaire pour cela de redéployer l’application. Les logpoints sont exécutés virtuellement, sans impact ou ni effet secondaire sur l’application en cours d’exécution.

#### <a name="to-create-a-logpoint"></a>Créer un logpoint

1. Cliquez avec le bouton droit sur une icône de snappoint (hexagone bleu) et choisissez **Paramètres**.

1. Dans la fenêtre des paramètres du snappoint, sélectionnez **Actions**.

    ![Créer un logpoint](../debugger/media/snapshot-logpoint.png)

1. Dans le champ **Message**, entrez le nouveau message de journal à consigner. Vous pouvez également évaluer des variables dans votre message de journal en les plaçant entre accolades.

    Si **Envoyer dans la fenêtre Sortie** est sélectionné, le message s’affiche dans la fenêtre Outils de diagnostic lorsque le logpoint est atteint.

    ![Données de logpoint dans la fenêtre Outils de diagnostic](../debugger/media/snapshot-logpoint-output.png)

    Si **Envoyer au journal des applications** est sélectionné, le message s’affiche partout où apparaissent les messages de `System.Diagnostics.Trace` (ou `ILogger` dans .NET Core), par exemple [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs), lorsque le logpoint est atteint.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris comment utiliser le Débogueur de capture instantanée pour les machines virtuelles Azure et les groupes de machines virtuelles identiques Azure. Peut-être souhaitez-vous en savoir plus sur cette fonctionnalité.

> [!div class="nextstepaction"]
> [Questions fréquentes (FAQ) sur le débogage d’instantané](../debugger/debug-live-azure-apps-faq.yml)
