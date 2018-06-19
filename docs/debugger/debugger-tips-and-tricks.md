---
title: Trucs et astuces dans le débogueur Visual Studio
description: Découvrir des conseils de productivité pour le débogueur Visual Studio
ms.custom: ''
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb4fb2c32f74a764e092e0e6f65685a358d64f54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927280"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Découvrez la productivité des conseils et astuces pour le débogueur dans Visual Studio

Lisez cette rubrique pour en savoir plus quelques conseils de productivité et astuces pour le débogueur Visual Studio. Pour examiner les fonctionnalités de base du débogueur, consultez [présentation des fonctionnalités de débogueur](../debugger/debugger-feature-tour.md). Dans cette rubrique, nous couvrent certaines zones qui ne sont pas inclus dans la visite guidée des fonctionnalités.

## <a name="pin-data-tips"></a>Conseils sur les données de code confidentiel

Si vous survolez fréquemment des conseils de données pendant le débogage, vous souhaiterez épingler l’info-bulle pour la variable accéder rapidement. La variable reste épinglée même après le redémarrage. Pour épingler l’info-bulle, cliquez sur l’icône d’épingle tout en pointant dessus. Vous pouvez épingler plusieurs variables.

![L’épinglage d’une info-bulle](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modifier votre code et continuer le débogage (c#, VB, C++)

Dans la plupart des langages pris en charge par Visual Studio, vous pouvez modifier votre code au milieu d’une session de débogage et continuer le débogage. Pour utiliser cette fonctionnalité, cliquez sur dans votre code avec votre curseur pendant la suspension dans le débogueur, vérifiez les modifications, appuyez sur **F5**, **F10**, ou **F11** pour continuer le débogage.

![Modifier et continuer le débogage](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Pour plus d’informations sur l’utilisation de la fonctionnalité et sur les limitations de fonctionnalités, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Déboguer les problèmes difficiles à reproduire

S’il est difficile ou du temps recréer un état particulier dans votre application, considérez que l’utilisation d’un point d’arrêt conditionnel peut aider à. Vous pouvez utiliser [points d’arrêt conditionnels](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) et filtrer les points d’arrêt pour éviter de rompre dans le code de votre application jusqu'à ce que l’application passe à l’état souhaité (par exemple, un état dans lequel une variable stocke des données erronées). Vous pouvez définir des conditions à l’aide d’expressions, les filtres, les nombres d’accès et ainsi de suite.

#### <a name="to-create-a-conditional-breakpoint"></a>Pour créer un point d’arrêt conditionnel

1. Cliquez sur une icône de point d’arrêt (la bille rouge) et choisissez **Conditions**.

2. Dans le **les paramètres de point d’arrêt** fenêtre, tapez une expression.

    ![Point d’arrêt conditionnel](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si vous êtes intéressé par un autre type de condition, sélectionnez **filtre** au lieu de **expression conditionnelle** dans les **les paramètres de point d’arrêt** boîte de dialogue et suivez le conseils de filtre.

## <a name="change-the-execution-flow"></a>Modifier le flux d’exécution

Avec le débogueur suspendue sur une ligne de code, utilisez la souris de saisir le pointeur de la flèche jaune à gauche. Déplacez le pointeur de la flèche jaune vers un autre point dans le chemin d’accès de l’exécution de code. Puis vous utilisez F5 ou une commande d’étape pour continuer l’exécution de l’application.

![Déplacez le pointeur d’exécution](../debugger/media/dbg-tour-move-the-execution-pointer.gif "déplacer le pointeur d’exécution")

En modifiant le flux d’exécution, vous pouvez effectuer diverses tâches telles que les chemins d’exécution de code différent de test ou réexécutez le code sans redémarrer le débogueur.

> [!WARNING]
> Fréquence à laquelle vous devez être prudent avec cette fonctionnalité, et un avertissement s’affiche dans l’info-bulle. Vous pouvez voir les autres avertissements, trop. Déplacer le pointeur ne peut pas rétablir votre application à un état antérieur de l’application.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Suivre un objet hors de portée (c#, Visual Basic)

Il est facile d’afficher des variables à l’aide des fenêtres du débogueur, comme la **espion** fenêtre. Toutefois, quand une variable est hors de portée dans le **espion** fenêtre, vous pouvez remarquer qu’il est grisé. Dans certains scénarios d’application, la valeur d’une variable peut changer même quand la variable est hors de portée, et vous pouvez souhaiter surveiller de près (par exemple, une variable peut que le garbage collector). Vous pouvez suivre la variable en créant un ID d’objet pour lui dans la **espion** fenêtre.

#### <a name="to-create-an-object-id"></a>Pour créer un ID d’objet

1.  Définissez un point d’arrêt vers une variable que vous souhaitez suivre.

2.  Démarrez le débogueur (**F5**) et arrêter au point d’arrêt.

3. Recherchez la variable dans le **variables locales** fenêtre (**Déboguer > Windows > variables locales**), avec le bouton droit de la variable, puis sélectionnez **générer ID de l’objet**.

    ![Créer un ID d’objet](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Le symbole **$** et un nombre s’affichent alors dans la fenêtre **Variables locales** . Cette variable est l’ID d’objet.
  
5.  Avec le bouton droit de la variable ID d’objet et choisissez **ajouter un espion**.

Pour plus d’informations, consultez [créer un ID d’objet](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Afficher les valeurs de retour pour les fonctions

Pour afficher les valeurs de retour pour vos fonctions, examinez les fonctions qui s’affichent dans le **automatique** fenêtre pendant que vous sont pas à pas détaillé dans votre code. Pour afficher la valeur de retour pour une fonction, assurez-vous que la fonction que vous êtes intéressé a déjà été exécuté (appuyez sur **F10** qu’une seule fois si vous êtes actuellement arrêté sur l’appel de fonction). Si la fenêtre est fermée, utilisez **Déboguer > Windows > automatique** pour ouvrir le **automatique** fenêtre.

![Automatique fenêtre](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

En outre, vous pouvez entrer des fonctions dans le **exécution** pour afficher les valeurs de retour. (Ouvrez à l’aide de **Déboguer > Windows > exécution**.)

![Fenêtre exécution](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Vous pouvez également utiliser [pseudo-variables](../debugger/pseudovariables.md) dans les **espion** et **exécution** fenêtre, tel que `$ReturnValue`.

## <a name="string_visualizer"></a>Inspecter les chaînes dans un visualiseur

Lorsque vous travaillez avec des chaînes, il peut être utile d’afficher la totalité de la chaîne mise en forme. Pour afficher un texte brut, la chaîne JSON, HTML ou XML, cliquez sur l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur") tout en pointant sur une variable qui contient une valeur de chaîne.

![Ouvrir un visualiseur de chaîne](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualiseur de chaîne peut vous aider à déterminer si une chaîne est mal formée, selon le type de chaîne. Par exemple, une valeur vide **valeur** champ indique la chaîne n’est pas reconnue par le type de visualiseur. Pour plus d’informations, consultez [visualiseur de chaîne, boîte de dialogue](../debugger/string-visualizer-dialog-box.md).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Pour d’autres types tels que les objets WPF qui s’affichent dans les fenêtres du débogueur, vous pouvez également ouvrir des visualiseurs.

## <a name="break-into-code-on-handled-exceptions"></a>Arrêter le code sur des exceptions

Le débogueur s’arrête dans votre code sur les exceptions non gérées. Toutefois, les exceptions traitées (tels que les exceptions qui se produisent dans un `try/catch` bloc) peut également être une source de bogues et vous pouvez examiner quand elles se produisent. Vous pouvez configurer le débogueur s’arrête dans du code pour les exceptions et en configurant les options dans le **paramètres d’Exception** boîte de dialogue. Ouvrez cette boîte de dialogue en choisissant **Déboguer > Windows > Paramètres d’Exception**.

Le **paramètres d’Exception** boîte de dialogue vous permet d’indiquer le débogueur s’arrête dans du code sur des exceptions spécifiques. Dans l’illustration ci-dessous, le débogueur s’arrête dans votre code chaque fois qu’un `System.NullReferenceException` se produit. Pour plus d’informations, consultez [gestion des exceptions](../debugger/managing-exceptions-with-the-debugger.md).

![Boîte de dialogue Paramètres exception](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Déboguer des blocages et des conditions de concurrence

Si vous devez déboguer des types de problèmes qui sont communes à des applications multithreads, il vous aide souvent à afficher l’emplacement des threads pendant le débogage. Ce faire, vous pouvez utiliser facilement les **afficher les Threads dans la Source** bouton.

#### <a name="to-show-threads-in-your-source-code"></a>Pour afficher les threads dans votre code source

1.  Pendant le débogage, cliquez sur le **afficher les Threads dans la Source** bouton ![afficher les Threads dans la Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dans les **déboguer** barre d’outils.
  
2.  Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous voyez un *marqueur de thread* icône ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") qui ressemblant à. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.

    Notez qu’un marqueur de thread peut être partiellement masqué par un point d’arrêt.
  
3.  Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu.

    Vous pouvez également afficher l’emplacement de threads dans le [la fenêtre Piles parallèles](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examiner les charges utiles pour les services web et des ressources du réseau (UWP)

Dans les applications UWP, vous pouvez analyser les opérations réseau effectuées à l’aide de la `Windows.Web.Http` API. Vous pouvez utiliser cet outil pour vous aider à déboguer des services web et des ressources réseau. Pour utiliser l’outil, sélectionnez **Déboguer > profileur**. Sélectionnez **réseau**, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario qui utilise `Windows.Web.Http`, puis choisissez **Arrêter la collecte** pour générer le rapport.

![Réseau de l’utilisation de l’outil de profilage](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Sélectionnez une opération dans la vue du résumé pour afficher des informations plus détaillées.

![Détails de l’outil de l’utilisation du réseau](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Pour plus d’informations, consultez [Utilisation du réseau](../profiling/network-usage.md).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Get familiarisé avec la façon dont le débogueur s’attache à votre application

Pour attacher à votre application en cours d’exécution, le débogueur charge les fichiers de symboles (.pdb) générés pour exactement identique à celle de l’application que vous essayez de déboguer. Dans certains scénarios, quelques connaissances des fichiers de symboles peut être utile. Vous pouvez examiner la façon dont Visual Studio charge les fichiers de symboles à l’aide de la **Modules** fenêtre.

Ouvrez le **Modules** fenêtre pendant le débogage en sélectionnant **Déboguer > Windows > Modules**. Le **Modules** fenêtre peut vous indiquer les modules que le débogueur va traiter comme du code utilisateur, ou [ *mon Code*](../debugger/just-my-code.md)et le symbole de chargement de l’état du module. Dans la plupart des scénarios, le débogueur recherche automatiquement les fichiers de symboles pour le code utilisateur, mais si vous souhaitez pas à pas détaillé (ou déboguer) du code .NET framework, le code système ou code de bibliothèque tierce, des étapes supplémentaires sont requises pour obtenir les fichiers de symbole correct.

![Afficher les informations de symbole dans la fenêtre Modules](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Vous pouvez charger les informations de symbole directement à partir de la **Modules** fenêtre en cliquant et en choisissant **charger les symboles**.

Parfois, les développeurs d’applications livrer des applications sans les fichiers de symboles correspondants (pour réduire l’encombrement), tout en conservant une copie du symbole de correspondance de fichiers pour la build afin que pouvoir déboguer une version ultérieure.

Pour savoir comment le débogueur classe code comme du code utilisateur, consultez [uniquement mon Code](../debugger/just-my-code.md). Pour plus d’informations sur les fichiers de symboles, consultez [spécifier les symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>En savoir plus

Pour des conseils supplémentaires et des astuces et des informations plus détaillées, consultez ces billets de blog :

- [7 hacks connus plus petit pour le débogage dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gems masqués dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Voir aussi
[Raccourcis clavier](../ide/tips-and-tricks-for-visual-studio.md)
