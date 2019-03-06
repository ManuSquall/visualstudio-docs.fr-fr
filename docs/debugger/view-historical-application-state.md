---
title: Afficher l’état précédent de l’application à l’aide d’IntelliTrace
description: Découvrez comment prendre des captures instantanées et les voir avec le retour en arrière IntelliTrace
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf319dd00048a4abf6cc4e3806845200c9eefc64
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703576"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Inspecter les précédents états des applications à l’aide du retour en arrière IntelliTrace dans Visual Studio (Visual Studio Enterprise)

Le retour en arrière IntelliTrace crée automatiquement une capture instantanée de votre application à chaque point d’arrêt et chaque étape du débogueur. Les captures instantanées enregistrées vous permettent de revenir à des étapes ou points d’arrêt précédents pour afficher un état antérieur de l’application. Le retour en arrière IntelliTrace peut vous faire gagner du temps quand vous souhaitez afficher un état précédent de l’application sans avoir à redémarrer le débogage ou à recréer l’état de l’application souhaité.

Le retour en arrière IntelliTrace est disponible à partir de Visual Studio Enterprise 2017 version 15.5 et versions ultérieures, et il nécessite la Mise à jour anniversaire Windows 10 ou version ultérieure. La fonctionnalité est actuellement prise en charge pour le débogage d’ASP.NET, de WinForms, de WPF, des applications console gérées et des bibliothèques de classes managées. À compter de Visual Studio 2017 Enterprise version 15.7, la fonctionnalité est également prise en charge pour ASP.NET Core et .NET Core. À compter de Visual Studio 2017 Enterprise version 15.9 Preview 2, la fonctionnalité est également pris en charge pour les applications natives ciblant Windows. Le débogage des applications UWP n’est pas pris en charge actuellement.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Activer les captures instantanées et les événements IntelliTrace
> * Parcourir les événements à l’aide des commandes Revenir en arrière et Étape suivante
> * Afficher des captures instantanées d’événements

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Activer le mode Événements et captures instantanées IntelliTrace

1. Ouvrez votre projet dans Visual Studio Enterprise.

1. Accédez à **Outils** > **Options** > **Paramètres IntelliTrace**, puis sélectionnez l’option **Événements et instantanés IntelliTrace**.

    À compter de Visual Studio 2017 Enterprise version 15.9 Preview 2, cette option se nomme **Instantanés IntelliTrace (Managé et natif)**.

    ![Activer le mode Événements et captures instantanées IntelliTrace](../debugger/media/intellitrace-enable-snapshots.png "Activer le mode Événements et captures instantanées IntelliTrace")

1. Si vous souhaitez configurer des options pour afficher les captures instantanées en cas d’exception, choisissez **IntelliTrace** > **Avancé** dans la boîte de dialogue **Options**.

    Ces options sont disponibles à partir de Visual Studio 2017 Enterprise version 15.7.

    ![Configurer le comportement pour les captures instantanées en cas d’exception](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Quand vous activez les événements et captures instantanées, la création de captures instantanées en cas d’exception est également activée par défaut. Vous pouvez désactiver les captures instantanées en cas d’exception en désélectionnant **Collecte des captures instantanées pour les événements d’exception**. Quand cette fonctionnalité est activée, des captures instantanées sont créées pour les exceptions non gérées. Pour les exceptions gérées, des captures instantanées sont créées uniquement si l’exception est levée et qu’il ne s’agit pas d’une deuxième levée d’une exception précédemment levée. Vous pouvez définir un nombre maximal de captures instantanées en cas d’exception en sélectionnant une valeur dans la liste déroulante. La valeur maximale s’applique à chaque fois que votre application passe en mode Arrêt (par exemple quand elle atteint un point d’arrêt).

    > [!NOTE]
    > Des captures instantanées sont créées uniquement pour les événements d’exception enregistrés par IntelliTrace. Pour le code managé, vous pouvez spécifier quels événements IntelliTrace enregistre en sélectionnant **Outils** > **Options** > **Événements IntelliTrace**.

1. Dans votre projet, définissez un ou plusieurs points d’arrêt et démarrez le débogage (appuyez sur **F5**), ou démarrez le débogage en parcourant votre code (**F10** ou **F11**).

    IntelliTrace crée une capture instantanée du processus de l’application à chaque étape du débogueur, événement de point d’arrêt et événement d’exception non gérée. Ces événements sont enregistrés sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**, avec d’autres événements IntelliTrace. Pour ouvrir cette fenêtre, choisissez **Déboguer** > **Windows** > **Afficher les Outils de diagnostic**.

    Une icône représentant un appareil photo s’affiche en regard des événements pour lesquels des captures instantanées sont disponibles.

    ![Onglet Événements avec des captures instantanées](../debugger/media/intellitrace-events-tab-with-snapshots.png "Onglet Événements avec des captures instantanées au niveau des points d’arrêt et des étapes")

    Pour des raisons de performances, aucune capture instantanée n’est créée quand vous effectuez un pas à pas très rapide. Si aucune icône d’appareil photo ne s’affiche en regard de l’étape, essayez d’avancer plus lentement.

## <a name="navigate-and-view-snapshots"></a>Parcourir et afficher les captures instantanées

1. Parcourez les événements à l’aide des boutons **Revenir en arrière (Alt + [)** et **Étape suivante (Alt + ])** situés dans la barre d’outils Déboguer.

    Utilisez ces boutons pour accéder aux événements figurant sous l’onglet **Événements** de la fenêtre **Outils de diagnostic**. Quand vous passez à l’étape précédente ou suivante d’un événement, vous activez automatiquement le [débogage d’historique](../debugger/historical-debugging.md) pour l’événement sélectionné.

    ![Boutons Revenir en arrière et Étape suivante](../debugger/media/intellitrace-step-back-icons-description.png "Boutons Revenir en arrière et Étape suivante")

    Quand vous avancez ou revenez en arrière, Visual Studio entre mode débogage d’historique. Dans ce mode, le contexte du débogueur bascule vers le moment où l’événement sélectionné a été enregistré. Visual Studio déplace également le pointeur vers la ligne de code correspondante dans la fenêtre source.

    À partir de cette vue, vous pouvez inspecter les valeurs dans les fenêtres **Pile des appels**, **Variables locales**, **Automatique** et **Espion**. Vous pouvez également pointer sur les variables pour afficher des DataTips et effectuer l’évaluation des expressions dans la fenêtre **Exécution**. Les données affichées sont celles provenant de la capture instantanée du processus de l’application créée à ce moment dans le temps.

    Ainsi, par exemple, si vous avez atteint un point d’arrêt et avancé d’une étape (**F10**), le bouton **Revenir en arrière** place Visual Studio en mode d’historique à la ligne de code correspondant au point d’arrêt.

    ![Activation du mode historique sur un événement avec une capture instantanée](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Activation du mode historique sur un événement avec une capture instantanée")

2. Pour revenir à l’exécution en direct, choisissez **Continuer (F5)** ou cliquez sur le lien **Revenir au débogage dynamique** dans la barre d’informations.

3. Vous pouvez également afficher une capture instantanée à partir de l’onglet **Événements**. Pour ce faire, sélectionnez un événement avec une capture instantanée, puis cliquez sur **Activer le débogage d’historique**.

    ![Activer le débogage d’historique sur un événement](../debugger/media/intellitrace-activate-historical-debugging.png "Activer le débogage d’historique sur un événement")

    Contrairement à la commande **Définir l’instruction suivante**, l’affichage d’une capture instantanée ne réexécute pas votre code ; il vous donne une vue statique de l’état de l’application à un point dans le temps qui s’est produit dans le passé.

    ![Vue d’ensemble du retour en arrière IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Vue d’ensemble du retour en arrière IntelliTrace")

    Pour en savoir plus sur la façon d’inspecter des variables dans Visual Studio, consultez la [visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md).

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>En quoi la fonctionnalité Retour en arrière d’IntelliTrace diffère-t-elle du mode Événements IntelliTrace uniquement ?

IntelliTrace en mode Événements uniquement vous permet d’activer le débogage d’historique sur les points d’arrêt et les étapes du débogueur. Toutefois, IntelliTrace capture les données des fenêtres **Variables locales** et **Automatique** uniquement si ces fenêtres sont ouvertes, et il capture uniquement les données qui sont développées et dans la vue. En mode Événements uniquement, vous avez rarement une vue complète des variables et des objets complexes. De plus, l’évaluation des expressions et l’affichage des données dans la fenêtre **Espion** ne sont pas prises en charge.

En mode Événements et captures instantanées, IntelliTrace crée une capture instantanée complète du processus de l’application, y compris les objets complexes. Sur une ligne de code, vous pouvez voir les mêmes informations que si vous étiez arrêtés à un point d’arrêt (et peu importe si vous avez auparavant développé les informations). L’évaluation des expressions est également prise en charge lors de l’affichage d’une capture instantanée.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>Qu’est l’impact de cette fonctionnalité sur les performances ? 

L’impact sur les performances globales du pas à pas dépend de votre application. La surcharge liée à la création de capture instantanée est d’environ 30 ms. Quand une capture instantanée est créée, le processus de l’application est dupliqué et la copie dupliquée est suspendue. Quand vous affichez une capture instantanée, Visual Studio s’attache à la copie dupliquée du processus. Pour chaque capture instantanée, Visual Studio copie uniquement la table des pages et définit les pages sur « copie pour écriture ». Si des objets sur le tas changent entre les étapes du débogueur avec des captures instantanées associées, la table des pages correspondante est alors copiée, ce qui entraîne un coût mémoire minimal. Si Visual Studio détecte qu’il n’y a pas suffisamment de mémoire pour créer une capture instantanée, il n’en crée pas.

## <a name="known-issues"></a>Problèmes connus
* Si vous utilisez le mode Événements et captures instantanées IntelliTrace sur des versions de Windows antérieures à Windows 10 Fall Creators Update (RS3) et que la cible de plateforme de débogage de l’application est définie sur x86, IntelliTrace ne crée pas de capture instantanée.

    Solutions de contournement :
  * Si vous exécutez la version 10.0.14393.2273 Mise à jour anniversaire Windows 10 (RS1) ou version antérieure, [installez KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Si vous exécutez la version 10.0.15063.1112 Windows 10 Creators Update (RS2) ou version antérieure, [installez KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Installer ou mettre à niveau vers Windows 10 Fall Creators Update (RS3).
  * Ou encore :
    1. Installez l’ensemble d’outils VC ++ 2015.3 v140 du composant poste de travail (x86, x64) à partir du programme d’installation de Visual Studio.
    2. Générez l’application cible.
    3. À partir de la ligne de commande, utilisez l’outil editbin afin de définir l’indicateur `Largeaddressaware` pour l’exécutable cible. Par exemple, vous pouvez utiliser cette commande (après avoir mis à jour le chemin) : "C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. Pour démarrer le débogage, appuyez sur **F5**. À présent, des captures instantanées peuvent être créées au niveau des points d’arrêt et des étapes du débogueur.

       > [!Note]
       > L’indicateur `Largeaddressaware` doit être défini chaque fois que le fichier exécutable est regénéré avec des modifications.

* Quand une capture instantanée du processus de l’application est créée sur une application qui utilise un fichier mappé en mémoire persistant, le processus avec la capture instantanée détient un verrou exclusif sur le fichier mappé en mémoire (même après que le processus parent a libéré son verrou). Les autres processus peuvent toujours lire le fichier mappé en mémoire, mais ils ne peuvent pas y écrire.

    Solution de contournement :
    * Effacez toutes les captures instantanées en mettant fin à la session de débogage.

* Lors du débogage d’une application dont le processus a un grand nombre de régions de mémoire uniques, telle qu’une application qui charge un grand nombre de DLL, les performances du pas à pas avec les captures instantanées activées peuvent être affectées. Ce problème sera résolu dans une version ultérieure de Windows. Si vous rencontrez ce problème, écrivez-nous à stepback@microsoft.com.

* Lors de l’enregistrement d’un fichier avec **Déboguer > IntelliTrace > Enregistrer la session IntelliTrace** en mode Événements et captures instantanées, les données supplémentaires capturées à partir de captures instantanées ne sont pas disponibles dans le fichier .itrace. Lors des événements de point d’arrêt et d’étape, vous voyez les mêmes informations que si vous aviez enregistré le fichier en mode Événements IntelliTrace uniquement.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris comment utiliser le retour en arrière IntelliTrace. Vous souhaiterez peut-être en savoir plus sur les autres fonctionnalités d’IntelliTrace.

> [!div class="nextstepaction"]
> [Fonctionnalités IntelliTrace](../debugger/intellitrace-features.md)
