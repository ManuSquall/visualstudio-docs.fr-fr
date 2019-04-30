---
title: Temps voyage débogage en direct ASP.NET des machines virtuelles Azure
description: Découvrez comment enregistrer et relire les applications ASP.NET en production sur des machines virtuelles à l’aide du débogueur de capture instantanée.
ms.custom: ''
ms.date: 04/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 3a81f6aa138b361a44a272ebda3557d27a914c64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854173"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Enregistrer et relire les applications ASP.NET en production sur des machines virtuelles à l’aide du débogueur de capture instantanée

L’aperçu de débogage de voyage temps (TTD) dans Visual Studio Enterprise offre la possibilité d’enregistrer une application Web en cours d’exécution sur une Machine virtuelle (VM) Azure et avec précision reconstruire, puis relire le chemin d’exécution. TTD s’intègre avec le débogueur de capture instantanée et vous permet de revenir en arrière et de relire chaque ligne de code n’importe quel nombre de fois que vous le souhaitez, vous aider à isoler et identifier les problèmes qui peuvent se produire uniquement dans les environnements de production.

Capture d’un enregistrement du temps de détection s’arrête pas l’application. Toutefois, l’enregistrement de TDD ajoute une surcharge significative à votre processus en cours d’exécution, il ralentit l’en fonction de facteurs tels que la taille du processus et le nombre de threads actifs.

Cette fonctionnalité est disponible en version préliminaire de la version de Visual Studio 2019 avec une licence go live.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Démarrer le débogueur de capture instantanée avec le temps voyage débogage activé
> * Définir un point d’ancrage et de collecter une durée de voyage d’enregistrement
> * Démarrez le débogage d’une heure d’enregistrement de voyage

## <a name="prerequisites"></a>Prérequis

* Débogage de trajet de temps pour les Machines virtuelles Azure (VM) est uniquement disponible pour Visual Studio 2019 Enterprise ou une version ultérieure avec le **charge de travail de développement Azure**. (Dans l’onglet **Composants individuels**, vous le trouverez sous **Débogage et test** > **Débogueur de capture instantanée**.)

    S’il n’est pas déjà installé, installez [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Débogage de trajet de temps est disponible pour les applications web de machine virtuelle Azure suivantes :
  * Applications ASP.NET (AMD64) en cours d’exécution sur .NET Framework 4.8 ou version ultérieure.

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Ouvrez votre projet et démarrer le débogueur de capture instantanée avec le temps voyage débogage activé

1. Ouvrez le projet pour lequel vous souhaitez collecter un temps d’enregistrement de voyage.

    > [!IMPORTANT]
    > Pour démarrer TTD, vous devez ouvrir le *même version de code source* qui est publié sur votre service de machine virtuelle Azure.

1. Choisissez **Déboguer > Joindre le Débogueur de capture instantanée…**. Sélectionnez la machine virtuelle Azure que votre application web est déployée sur et un compte de stockage Azure. Sélectionnez le **activer le démarrage du débogage voyage** option d’aperçu, puis cliquez sur **attacher**.

      ![Sélectionner une ressource Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La première fois que vous sélectionnez **Joindre le Débogueur de capture instantanée** pour votre machine virtuelle, IIS est redémarré automatiquement.

    Les métadonnées pour le **Modules** n’est pas activé initialement. Accédez à l’application web et le **démarrer la collecte** bouton devienne alors actif. Visual Studio est maintenant en mode Débogage de capture instantanée.

   ![Mode Débogage de capture instantanée](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > L’extension de site Application Insights prend également en charge le débogage de capture instantanée. Si un message d’erreur du type « extension de site obsolète » apparaît, voir [Conseils de résolution des problèmes et problèmes connus pour le débogage de capture instantanée](../debugger/debug-live-azure-apps-troubleshooting.md) pour effectuer une mise à niveau.

   Le **Modules** fenêtre vous montre que lorsque tous les modules sont chargés pour la machine virtuelle Azure (choisissez **Déboguer > Windows > Modules** pour ouvrir cette fenêtre).

   ![Fenêtre Vérifier les modules](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Définir un point d’ancrage et de collecter une durée de voyage d’enregistrement

1. Dans l’éditeur de code, cliquez sur la marge gauche dans une méthode qui que vous intéresse définir un point d’ancrage. Vérifiez que ce code pourra s’exécuter.

   ![Définir un snappoint](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Cliquez sur l’icône de point d’ancrage (la balle creuse) et choisissez **Actions**. Dans le **paramètres de cliché instantané** fenêtre, cliquez sur le **Action** case à cocher. Puis cliquez sur le **recueillir une trace de trajet de temps à la fin de cette méthode** case à cocher.

   ![Recueillir une trace de trajet de temps à la fin de la méthode](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Cliquez sur **Lancer la collecte** pour activer le snappoint.

   ![Activer le snappoint](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Prendre un instantané

Lorsqu’un point d’ancrage est allumé, il capture un instantané chaque fois qu’exécute la ligne de code où se trouve le point d’ancrage. Cette exécution peut être dû à une demande réelle sur votre serveur. Pour forcer l’activation du snappoint, accédez à la vue dans le navigateur de votre site web et effectuez l’une des actions correspondant à ce snappoint.

## <a name="start-debugging-a-time-travel-recording"></a>Démarrez le débogage d’une heure d’enregistrement de voyage

1. Lorsque le snappoint est atteint, une capture instantanée apparaît dans la fenêtre Outils de diagnostic. Pour ouvrir cette fenêtre, choisissez **Déboguer > Fenêtres > Afficher les Outils de diagnostic**.

   ![Ouvrir un snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Cliquez sur le lien Afficher l’instantané pour ouvrir le voyage d’enregistrement dans l’éditeur de code.
  
   Vous pouvez exécuter chaque ligne de code enregistrée par le TTD à l’aide de la **continuer** et **inverse continuer** boutons. En outre, le **déboguer** barre d’outils peut être utilisé pour **afficher l’instruction suivante**, **pas à pas détaillé**, **pas à pas principal**, **pas à pas sortant**, **Étape de nouveau**, **étape sur**, **étape régulariser**.

   ![Démarrer le débogage](../debugger/media/time-travel-debugging-step-commands.png)

   Vous pouvez également utiliser le **variables locales**, **espions**, et **pile des appels** windows et également évaluer des expressions.

   ![Inspecter les données de capture instantanée](../debugger/media/time-travel-debugging-start-debugging.png)

    Le site Web lui-même est toujours en direct et les utilisateurs finaux ne sont pas affectées par les activités TTD suivantes. Par défaut, le snappoint ne prend qu’une capture instantanée : dès que c’est fait, il se désactive. Si vous souhaitez prendre une autre capture instantanée sur le snappoint, vous pouvez le réactiver en cliquant sur **Mettre à jour la collecte**.

**Besoin d’aide ?** Voir les pages [Résolution des problèmes et problèmes connus](../debugger/debug-live-azure-apps-troubleshooting.md) et [FAQ du débogage de captures instantanées](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Définir un snappoint conditionnel

S’il vous est difficile de recréer un état particulier de votre application, vous pouvez utiliser un snappoint conditionnel. Points d’ancrage conditionnel vous aident à que éviter la collecte d’une heure déplacent d’enregistrement jusqu'à ce que l’application passe à l’état souhaité, par exemple lorsqu’une variable a une valeur particulière que vous souhaitez inspecter. [Vous pouvez définir des conditions d’utilisation d’expressions, filtres, ou nombre d’accès](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment collecter un voyage d’enregistrement pour les Machines virtuelles Azure. Voulez-vous en savoir plus sur le débogueur de capture instantanée.

> [!div class="nextstepaction"]
> [FAQ pour le débogage d’instantané](../debugger/debug-live-azure-apps-faq.md)