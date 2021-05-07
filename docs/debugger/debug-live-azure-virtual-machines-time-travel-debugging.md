---
title: Heure du débogage de Live ASP.NET sur une machine virtuelle Azure
description: Découvrez comment enregistrer et relire des applications ASP.NET en direct sur des machines virtuelles Azure à l’aide du Débogueur de capture instantanée.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
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
ms.openlocfilehash: f8aabb109de02a1beec326407472a841fe16425a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798451"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Enregistrer et relire des applications ASP.NET en direct sur des machines virtuelles Azure à l’aide du Débogueur de capture instantanée

La préversion de l’heure du débogage (TTD) dans Visual Studio Enterprise offre la possibilité d’enregistrer une application Web exécutée sur une machine virtuelle Azure, puis de reconstruire et relire le chemin d’exécution avec précision. TTD s’intègre au Débogueur de capture instantanée et vous permet de rembobiner et relire chaque ligne de code autant de fois que vous le souhaitez, ce qui vous permet d’isoler et d’identifier les problèmes qui peuvent se produire uniquement dans des environnements de production.

La capture d’un enregistrement TTD n’interrompt pas l’application. Toutefois, l’enregistrement TDD ajoute une surcharge significative à votre processus en cours d’exécution, ce qui le ralentit en fonction de facteurs qui incluent la taille du processus et le nombre de threads actifs.

Cette fonctionnalité est en version préliminaire pour la version de Visual Studio 2019 avec une licence Go Live.

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
> * Démarrer le Débogueur de capture instantanée avec l’heure à laquelle le débogage de voyage est activé
> * Définir un point d’ancrage et collecter un enregistrement d’heure de voyage
> * Démarrer le débogage d’un enregistrement de voyage horaire

## <a name="prerequisites"></a>Prérequis

* Le débogage du temps de déplacement pour les machines virtuelles Azure est disponible uniquement pour Visual Studio 2019 Enterprise ou version ultérieure avec la **charge de travail de développement Azure**. (Dans l’onglet **Composants individuels**, vous le trouverez sous **Débogage et test** > **Débogueur de capture instantanée**.)

    S’il n’est pas déjà installé, installez [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Le débogage du temps de voyage est disponible pour les applications Web d’ordinateur virtuel Azure suivantes :
  * Applications ASP.NET (AMD64) s’exécutant sur .NET Framework 4,8 ou version ultérieure.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Démarrer le Débogueur de capture instantanée avec l’heure à laquelle le débogage de voyage est activé

1. Ouvrez le projet pour lequel vous souhaitez collecter un enregistrement de l’heure.

    > [!IMPORTANT]
    > Pour démarrer TTD, vous devez ouvrir la *même version du code source* qui est publiée sur votre service de machine virtuelle Azure.

1. Choisissez **Déboguer > attacher débogueur de capture instantanée...**. Sélectionnez la machine virtuelle Azure sur laquelle votre application Web est déployée et un compte de stockage Azure. Sélectionnez l’option **activer l’aperçu du débogage** de l’heure de voyage, puis cliquez sur **attacher**.

      ![Sélectionner une ressource Azure](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > La première fois que vous sélectionnez **Joindre le Débogueur de capture instantanée** pour votre machine virtuelle, IIS est redémarré automatiquement.

    Les métadonnées des **modules** ne sont pas initialement activées. Accédez à l’application Web et le bouton **Démarrer la collection** devient alors actif. Visual Studio est maintenant en mode Débogage de capture instantanée.

   ![Mode Débogage de capture instantanée](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > L’extension de site Application Insights prend également en charge le débogage de capture instantanée. Si un message d’erreur du type « extension de site obsolète » apparaît, voir [Conseils de résolution des problèmes et problèmes connus pour le débogage de capture instantanée](../debugger/debug-live-azure-apps-troubleshooting.md) pour effectuer une mise à niveau.

   La fenêtre **modules** affiche le moment où tous les modules sont chargés pour la machine virtuelle Azure (choisissez **déboguer > modules Windows >** pour ouvrir cette fenêtre).

   ![Fenêtre Vérifier les modules](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Définir un point d’ancrage et collecter un enregistrement d’heure de voyage

1. Dans l’éditeur de code, cliquez sur la marge gauche dans une méthode qui vous intéresse pour définir un point d’ancrage. Vérifiez que ce code pourra s’exécuter.

   ![Définir un snappoint](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Cliquez avec le bouton droit sur l’icône point d’ancrage (la balle creuse) et choisissez **actions**. Dans la fenêtre **paramètres d’instantané** , activez la case à cocher **action** . Cliquez ensuite sur la case à cocher **collecter un suivi des voyages d’heure à la fin de cette méthode** .

   ![Collecter un suivi des voyages d’heure à la fin de la méthode](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Cliquez sur **Lancer la collecte** pour activer le snappoint.

   ![Activer le snappoint](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Prendre un instantané

Quand un point d’ancrage est activé, il capture un instantané à chaque fois que la ligne de code où le point d’ancrage est placé est exécutée. Cette exécution peut être due à une demande réelle sur votre serveur. Pour forcer l’activation du snappoint, accédez à la vue dans le navigateur de votre site web et effectuez l’une des actions correspondant à ce snappoint.

## <a name="start-debugging-a-time-travel-recording"></a>Démarrer le débogage d’un enregistrement de voyage horaire

1. Lorsque le snappoint est atteint, une capture instantanée apparaît dans la fenêtre Outils de diagnostic. Pour ouvrir cette fenêtre, choisissez **Déboguer > Fenêtres > Afficher les Outils de diagnostic**.

   ![Ouvrir un snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Cliquez sur le lien Afficher l’instantané pour ouvrir l’enregistrement de l’heure de voyage dans l’éditeur de code.
  
   Vous pouvez exécuter chaque ligne de code enregistrée par le TTD à l’aide des boutons **Continuer** et **inverser continuer** . En outre, la barre d’outils de **débogage** peut être utilisée pour **afficher l’instruction suivante**, **pas à** pas détaillé **, pas à** pas principal **, pas à pas principal, revenir** **en** arrière **, pas** **à pas précédent**.

   ![Démarrer le débogage](../debugger/media/time-travel-debugging-step-commands.png)

   Vous pouvez également utiliser les fenêtres **variables locales**, **espions** et **pile des appels** , ainsi que évaluer les expressions.

   ![Inspecter les données de capture instantanée](../debugger/media/time-travel-debugging-start-debugging.png)

    Le site Web lui-même est toujours actif et les utilisateurs finaux ne sont pas affectés par une activité TTD suivante. Par défaut, le snappoint ne prend qu’une capture instantanée : dès que c’est fait, il se désactive. Si vous souhaitez prendre une autre capture instantanée sur le snappoint, vous pouvez le réactiver en cliquant sur **Mettre à jour la collecte**.

**Besoin d’aide ?** Voir les pages [Résolution des problèmes et problèmes connus](../debugger/debug-live-azure-apps-troubleshooting.md) et [FAQ du débogage de captures instantanées](../debugger/debug-live-azure-apps-faq.yml).

## <a name="set-a-conditional-snappoint"></a>Définir un snappoint conditionnel

S’il vous est difficile de recréer un état particulier de votre application, vous pouvez utiliser un snappoint conditionnel. Les points d’ancrage conditionnelles vous permettent d’éviter de collecter un enregistrement de temps de voyage jusqu’à ce que l’application entre dans un état souhaité, par exemple quand une variable a une valeur particulière que vous souhaitez inspecter. [Vous pouvez définir des conditions à l’aide d’expressions, de filtres ou de nombres d’accès](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à collecter un enregistrement de temps pour les machines virtuelles Azure. Vous souhaiterez peut-être en savoir plus sur Débogueur de capture instantanée.

> [!div class="nextstepaction"]
> [Questions fréquentes (FAQ) sur le débogage d’instantané](../debugger/debug-live-azure-apps-faq.yml)