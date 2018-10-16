---
title: Afficher l’état précédent de l’application à l’aide d’IntelliTrace
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85b34fd85e8449949bb1e96efc1dd79aacbc1bd9
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48243950"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Inspecter les États d’application précédente à l’aide de revenir en arrière IntelliTrace dans Visual Studio

Événement d’étape, en arrière IntelliTrace prend automatiquement un instantané de votre application à chaque point d’arrêt et le débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

En arrière IntelliTrace est disponible à partir de Visual Studio Enterprise 2017 version 15.5 et versions ultérieures, et elle nécessite la mise à jour anniversaire de Windows 10 ou version ultérieure. La fonctionnalité est actuellement pris en charge pour le débogage ASP.NET, WinForms, WPF, les applications de console gérée et bibliothèques de classes managées. À compter de Visual Studio 2017 Enterprise version 15.7, la fonctionnalité est également pris en charge pour ASP.NET Core et .NET Core. Démarrage avec Visual Studio 2017 Enterprise version 15.9 Preview 2, la fonctionnalité est également pris en charge pour les applications ciblant Windows natives. Débogage des applications UWP n’est pas pris en charge actuellement.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Activer les événements Intellitrace et les captures instantanées
> * Accédez à l’aide des commandes de revenir en arrière et avant de l’étape des événements
> * Afficher les instantanés
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Activer le mode d’événements et instantanés IntelliTrace 

1. Ouvrez votre projet dans Visual Studio Enterprise.

1. Ouvrez **outils** > **Options** > **IntelliTrace** paramètres, puis sélectionnez l’option **IntelliTrace événements et instantanés** . 

    À compter de Visual Studio 2017 Enterprise version 15.9 Preview 2, cette option ne **instantanés IntelliTrace (natifs et managés)**. 

    ![Activer le mode d’événements IntelliTrace et les captures instantanées](../debugger/media/intellitrace-enable-snapshots.png "mode activer les événements IntelliTrace et les captures instantanées")

1. Si vous souhaitez configurer des options pour les instantanés de l’affichage sur les exceptions, choisissez **IntelliTrace** > **avancé** à partir de la **Options** boîte de dialogue.

    Ces options sont disponibles à partir de Visual Studio 2017 Enterprise version 15.7.

    ![Configurer le comportement pour les captures instantanées sur les exceptions](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Lorsque vous activez les événements et captures instantanées, création de captures instantanées sur les exceptions est également activée par défaut. Vous pouvez désactiver les captures instantanées sur les exceptions en désélectionnant **collecter des instantanés sur les événements d’exception**. Lorsque cette fonctionnalité est activée, les instantanés sont créés pour les exceptions non gérées. Pour les exceptions, les instantanés sont créés uniquement si l’exception est levée et si elle n’est pas un lever à nouveau d’une exception précédemment levée. Vous pouvez définir un nombre maximal d’instantanés sur les exceptions en sélectionnant une valeur dans la liste déroulante. La valeur maximale s’applique à chaque fois que votre application passe en mode arrêt (par exemple, quand votre application atteint un point d’arrêt).

    > [!NOTE]
    > Instantanés sont créés uniquement pour les événements d’exception qu’IntelliTrace enregistre. Pour le code managé, vous pouvez spécifier quels événements IntelliTrace enregistre en sélectionnant **outils** > **Options** > **événements IntelliTrace**.

1. Dans votre projet, définissez un ou plusieurs points d’arrêt et démarrer le débogage (appuyez sur **F5**), ou démarrer le débogage en parcourant votre code (**F10** ou **F11**).

    IntelliTrace prend un instantané du processus de l’application sur chaque étape du débogueur, un événement de point d’arrêt et un événement d’exception non gérée. Ces événements sont enregistrés dans le **événements** onglet dans le **outils de Diagnostic** fenêtre, ainsi que d’autres événements IntelliTrace. Pour ouvrir cette fenêtre, choisissez **déboguer** > **Windows** > **afficher les outils de Diagnostic**.

    Une icône représentant une caméra s’affiche en regard des événements pour lesquels des captures instantanées sont disponibles. 

    ![Onglet d’événements avec des captures instantanées](../debugger/media/intellitrace-events-tab-with-snapshots.png "onglet d’événements avec des captures instantanées sur des points d’arrêt et les étapes")

    Pour des raisons de performances, les captures instantanées ne sont pas prises lorsque vous parcourez très rapidement. Si aucune icône d’appareil photo s’affiche en regard de l’étape, avancez plus lentement.

## <a name="navigate-and-view-snapshots"></a>Accédez et afficher les captures instantanées

1. Naviguer entre les événements à l’aide de la **étape vers l’arrière (Alt + [)** et **étape suivante (Alt +])** boutons dans la barre d’outils de débogage.

    Ces boutons pour accéder aux événements qui s’affichent dans le **événements** onglet dans le **fenêtre Outils de Diagnostic**. Pas à pas détaillé vers l’arrière ou vers l’avant à un événement automatiquement Active [le débogage d’historique](../debugger/historical-debugging.md) sur l’événement sélectionné.

    ![Revenir en arrière et transférer des boutons](../debugger/media/intellitrace-step-back-icons-description.png "boutons étape précédente et étape suivante")

    Lorsque vous prenez du recul ou que vous avancez, Visual Studio entre mode débogage d’historique. Dans ce mode, le contexte du débogueur passe à la fois quand l’événement sélectionné a été enregistré. Visual Studio déplace également le pointeur vers la ligne de code dans la fenêtre source correspondante. 

    Dans cette vue, vous pouvez inspecter les valeurs dans le **pile des appels**, **variables locales**, **automatique**, et **espion** windows. Vous pouvez également pointer sur les variables pour afficher les DataTips et effectuer l’évaluation des expressions dans le **immédiat** fenêtre. Les données que vous voyez sont à partir de l’instantané du processus de l’application effectuée à ce stade dans le temps.

    Ainsi, par exemple, si vous avez atteint un point d’arrêt et de franchir une étape (**F10**), la **étape descendante** bouton place Visual Studio en mode d’historique à la ligne de code correspondant au point d’arrêt. 

    ![Mode historique d’activation sur un événement avec un instantané](../debugger/media/intellitrace-historical-mode-with-snapshot.png "mode historique d’activation sur un événement avec un instantané")

2. Pour revenir à l’exécution en direct, choisissez **continuer (F5)** ou cliquez sur le **revenir au débogage réel** lien dans la barre d’informations. 

3. Vous pouvez également afficher un instantané à partir de la **événements** onglet. Pour ce faire, sélectionnez un événement avec un instantané, puis cliquez sur **activer le débogage d’historique**.

    ![Activer le débogage d’historique sur un événement](../debugger/media/intellitrace-activate-historical-debugging.png "activer le débogage d’historique sur un événement")

    Contrairement à la **définir l’instruction suivante** commande, affichage d’un instantané ne réexécute pas votre code ; il vous donne une vue statique de l’état de l’application à un point dans le temps qui s’est produite dans le passé.

    ![Vue d’ensemble de revenir en arrière IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "vue d’ensemble de revenir en arrière IntelliTrace")

    Pour en savoir plus sur la façon d’inspecter des variables dans Visual Studio, consultez [visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>Comment les en arrière IntelliTrace est différent du mode d’uniquement les événements IntelliTrace ?

IntelliTrace en mode uniquement les événements vous permet d’activer le débogage d’historique sur les points d’arrêt et les étapes du débogueur. Toutefois, elle permet de capturer uniquement les données dans le **variables locales** et **automatique** windows si les fenêtres sont ouvertes, et elle capture uniquement les données qui sont développées et dans la vue. En mode uniquement les événements, souvent pas avoir une vue complète des variables et des objets complexes. En outre, expression d’évaluation et affichage des données dans le **espion** fenêtre n’est pas prise en charge. 

En mode d’événements et captures instantanées, elle permet de capturer l’intégralité de l’instantané du processus de l’application, y compris des objets complexes. Sur une ligne de code, vous pouvez voir les mêmes informations que si vous ont été arrêtées à un point d’arrêt (et il n’a pas d’importance si vous avez précédemment développés les informations). Évaluation de l’expression est également pris en charge lors de l’affichage d’un instantané.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Qu’est l’impact sur les performances de cette fonctionnalité ? 

L’impact sur les performances globales du pas à pas dépend de votre application. La surcharge de prendre un instantané est environ 30 ms. Lorsqu’un instantané est créé, le processus de l’application est dupliqué et la copie dupliquée est suspendue. Lorsque vous affichez un instantané, Visual Studio s’attache à la copie dupliquée du processus. Pour chaque instantané, Visual Studio copie uniquement la table des pages et définit les pages à la copie sur écriture. Si les objets sur le tas changent entre les étapes du débogueur avec des instantanés associés, la table des pages respectives est ensuite copiée, ce qui entraîne un coût de la mémoire minimale. Si Visual Studio détecte l’absence de suffisamment de mémoire pour prendre un instantané, il ne prend pas un.
 
## <a name="known-issues"></a>Problèmes connus  
* Si vous utilisez le mode d’événements et instantanés IntelliTrace sur les versions de Windows antérieures à Windows 10 Fall Creators Update (RS3), et si la cible de plateforme de débogage de l’application est définie sur x86, IntelliTrace ne prend pas de captures instantanées.

    Solutions de contournement :
    * Si vous êtes sur la mise à jour anniversaire Windows 10 (RS1) et inférieur à la version 10.0.14393.2273, [installer KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
    * Si vous êtes sur Windows 10 Creators Update (RS2) et inférieur à la version 10.0.15063.1112, [installer KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
    * Installer ou mettre à niveau vers Windows 10 Fall Creators Update (RS3). 
    * Vous pouvez également : 
        1. Installez l’ensemble d’outils VC ++ 2015.3 v140 du composant poste de travail (x86, x64) à partir du programme d’installation de Visual Studio.
        2. Générez l’application cible.
        3. À partir de la ligne de commande, utilisez l’outil editbin pour définir le `Largeaddressaware` indicateur pour l’exécutable cible. Par exemple, vous pouvez utiliser cette commande (après la mise à jour le chemin d’accès) : « C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe » /Largeaddressaware « C:\Path\To\Application\app.exe ».
        4. Pour démarrer le débogage, appuyez sur **F5**. Désormais, les instantanés sont créés sur des points d’arrêt et les étapes du débogueur.

        > [!Note]
        > Le `Largeaddressaware` l’indicateur doit être défini à chaque fois que le fichier exécutable est regénéré avec des modifications.

* Lorsqu’un instantané du processus de l’application est créé sur une application qui utilise un fichier mappé en mémoire persistant, le processus avec l’instantané détient un verrou exclusif sur le fichier mappé en mémoire (même après que le traitement parent a publié son verrou). Autres processus sont toujours en mesure de lire, mais pas écrire, dans le fichier mappé en mémoire.

    Solution de contournement :
    * Effacer toutes les captures instantanées en mettant fin à la session de débogage. 

* Lors du débogage d’une application dont le processus a un grand nombre de régions de mémoire unique, tel qu’une application qui charge un grand nombre de DLL, pas à pas détaillé des performances avec des captures instantanées activées peuvent être affectées. Ce problème sera résolu dans une future version de Windows. Si vous rencontrez ce problème, nous contacter à stepback@microsoft.com. 

* Lors de l’enregistrement d’un fichier avec **Déboguer > IntelliTrace > session IntelliTrace enregistrer** en mode d’événements et captures instantanées, les données supplémentaires capturées à partir d’instantanés ne sont pas disponibles dans le fichier .itrace. Sur les événements de point d’arrêt et d’étape, vous consultez les mêmes informations que si vous avez enregistré le fichier en mode d’uniquement les événements IntelliTrace. 

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris comment utiliser IntelliTrace revenir en arrière. Voulez-vous en savoir plus sur les autres fonctionnalités d’IntelliTrace.

> [!div class="nextstepaction"]
> [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)
