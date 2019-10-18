---
title: Trucs et astuces dans le débogueur
description: En savoir plus sur certaines des fonctionnalités moins connues prises en charge par le débogueur Visual Studio
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92d1c327c168bfd2881ad014b7f9ab87f771b95d
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536077"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Découvrez des trucs et astuces de productivité pour le débogueur dans Visual Studio

Lisez cette rubrique pour en savoir plus sur les astuces et astuces de productivité pour le débogueur Visual Studio. Pour découvrir les fonctionnalités de base du débogueur, consultez tout d' [abord le débogueur](../debugger/debugger-feature-tour.md). Dans cette rubrique, nous aborderons certains domaines qui ne sont pas inclus dans la visite guidée des fonctionnalités.

## <a name="pin-data-tips"></a>Épingler des conseils sur les données

Si vous pointez fréquemment sur des conseils de données pendant le débogage, vous souhaiterez peut-être épingler la bulle de données de la variable pour obtenir un accès rapide. La variable reste épinglée même après le redémarrage. Pour épingler la bulle de données, cliquez sur l’icône d’épingle en pointant dessus. Vous pouvez épingler plusieurs variables.

![Épinglage d’une bulle d’informations](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modifier votre code et continuer le débogage (C#, VB, C++)

Dans la plupart des langages pris en charge par Visual Studio, vous pouvez modifier votre code au milieu d’une session de débogage et poursuivre le débogage. Pour utiliser cette fonctionnalité, cliquez sur votre code à l’aide de votre curseur tout en étant suspendu dans le débogueur, apportez des modifications, puis appuyez sur **F5**, **F10**ou **F11** pour continuer le débogage.

![Modifier & continuer le débogage](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Pour plus d’informations sur l’utilisation de la fonctionnalité et sur les limitations relatives aux fonctionnalités, consultez [modifier & continuer](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Modifier le code XAML et continuer le débogage

Pour modifier le code XAML pendant une session de débogage, consultez [écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML](xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problèmes de débogage difficiles à reproduire

S’il est difficile ou fastidieux de recréer un état particulier dans votre application, déterminez si l’utilisation d’un point d’arrêt conditionnel peut être utile. Vous pouvez utiliser des points d’arrêt [conditionnels](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) et filtrer les points d’arrêt pour éviter une rupture dans le code de votre application jusqu’à ce que l’application entre dans un état souhaité (par exemple, un État dans lequel une variable stocke des données incorrectes). Vous pouvez définir des conditions à l’aide d’expressions, de filtres, de nombres d’accès, etc.

#### <a name="to-create-a-conditional-breakpoint"></a>Pour créer un point d’arrêt conditionnel

1. Cliquez avec le bouton droit sur une icône de point d’arrêt (la boule rouge) et choisissez **conditions**.

2. Dans la fenêtre **paramètres de point d’arrêt** , tapez une expression.

    ![Point d’arrêt conditionnel](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si vous êtes intéressé par un autre type de condition, sélectionnez **filtre** au lieu de **expression conditionnelle** dans la boîte de dialogue **paramètres de point d’arrêt** , puis suivez les conseils de filtre.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurer les données à afficher dans le débogueur

Pour C#, Visual Basic et C++ (C++code/CLI uniquement), vous pouvez indiquer au débogueur les informations à afficher à l’aide de l’attribut [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . Pour C++ le code, vous pouvez faire de même avec les [visualisations Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Changer le flux d’exécution

Lorsque le débogueur est suspendu sur une ligne de code, utilisez la souris pour saisir le pointeur en forme de flèche jaune sur la gauche. Déplacez le pointeur en forme de flèche jaune vers un autre point dans le chemin d’exécution du code. Ensuite, vous utilisez F5 ou une commande Step pour continuer à exécuter l’application.

![Déplacer le pointeur d’exécution](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Déplacer le pointeur d’exécution")

En changeant le flux d’exécution, vous pouvez effectuer des opérations comme tester d’autres chemins d’exécution du code ou réexécuter du code sans devoir redémarrer le débogueur.

> [!WARNING]
> Vous devez rester prudent avec cette fonctionnalité, vous pouvez voir un avertissement dans l’info-bulle. Vous pouvez aussi en voir d’autres. Le déplacement du pointeur ne peut pas rétablir l’état antérieur de votre application.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Suivre un objet hors de portée (C#, Visual Basic)

Il est facile d’afficher des variables à l’aide de fenêtres du débogueur, comme la fenêtre **Espion** . Toutefois, lorsqu’une variable sort de l’étendue dans la fenêtre **Espion** , vous pouvez remarquer qu’elle est grisée. Dans certains scénarios d’application, la valeur d’une variable peut changer même lorsque la variable est hors de portée, et vous souhaiterez peut-être la regarder en détail (par exemple, une variable peut obtenir le garbage collector). Vous pouvez suivre la variable en créant un ID d’objet pour celle-ci dans la fenêtre **Espion** .

#### <a name="to-create-an-object-id"></a>Pour créer un ID d’objet

1. Définissez un point d’arrêt à proximité d’une variable dont vous souhaitez effectuer le suivi.

2. Démarrez le débogueur (**F5**) et arrêtez au point d’arrêt.

3. Recherchez la variable dans la fenêtre **variables locales** (**déboguer > les variables locales Windows >** ), cliquez avec le bouton droit sur la variable, puis sélectionnez **créer un ID d’objet**.

    ![Créer un ID d’objet](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Le symbole **$** et un nombre s’affichent alors dans la fenêtre **Variables locales** . Cette variable est l’ID d’objet.

5. Cliquez avec le bouton droit sur la variable d’ID d’objet et choisissez **Ajouter un espion**.

Pour plus d’informations, consultez [créer un ID d’objet](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Afficher les valeurs de retour pour les fonctions

Pour afficher les valeurs de retour de vos fonctions, examinez les fonctions qui s’affichent dans la fenêtre **automatique** pendant que vous exécutez pas à pas votre code. Pour afficher la valeur de retour d’une fonction, assurez-vous que la fonction qui vous intéresse a déjà été exécutée (appuyez sur **F10** une fois si vous êtes actuellement arrêté sur l’appel de fonction). Si la fenêtre est fermée, utilisez l' **> de débogage Windows > automatique** pour ouvrir la fenêtre **automatique** .

![Fenêtre automatique](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

En outre, vous pouvez entrer des fonctions dans la fenêtre **exécution** pour afficher les valeurs de retour. (Ouvrez-le à l’aide du **> de débogage Windows > immédiat**.)

![Exécution, fenêtre](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Vous pouvez également utiliser [Pseudo-variables](../debugger/pseudovariables.md) dans la fenêtre **Espion** et **exécution** , par exemple `$ReturnValue`.

## <a name="string_visualizer"></a>Inspecter des chaînes dans un visualiseur

Lorsque vous utilisez des chaînes, il peut être utile d’afficher l’intégralité de la chaîne mise en forme. Pour afficher une chaîne en texte brut, XML, HTML ou JSON, cliquez sur l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur") tout en pointant sur une variable contenant une valeur de chaîne.

![Ouvrir un visualiseur de chaîne](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualiseur de chaîne peut vous aider à déterminer si une chaîne est incorrecte, selon le type de chaîne. Par exemple, un champ de **valeur** vide indique que la chaîne n’est pas reconnue par le type de visualiseur. Pour plus d’informations, consultez [boîte de dialogue visualiseur de chaîne](../debugger/string-visualizer-dialog-box.md).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Pour quelques autres types tels que les objets DataSet et DataTable qui apparaissent dans les fenêtres du débogueur, vous pouvez également ouvrir un visualiseur intégré.

## <a name="break-into-code-on-handled-exceptions"></a>S’arrêter dans le code sur les exceptions gérées

Le débogueur s’arrête dans votre code sur les exceptions non gérées. Toutefois, les exceptions gérées (telles que les exceptions qui se produisent dans un bloc `try/catch`) peuvent également être une source de bogues et vous pouvez examiner quand elles se produisent. Vous pouvez configurer le débogueur pour qu’il s’arrête également dans le code pour les exceptions gérées, en configurant les options de la boîte de dialogue **paramètres d’exception** . Pour ouvrir cette boîte de dialogue, choisissez **Déboguer > paramètres d’exception Windows >** .

La boîte de dialogue **paramètres d’exception** vous permet d’indiquer au débogueur de s’arrêter dans du code sur des exceptions spécifiques. Dans l’illustration ci-dessous, le débogueur s’arrête dans votre code chaque fois qu’une `System.NullReferenceException` se produit. Pour plus d’informations, consultez [gestion des exceptions](../debugger/managing-exceptions-with-the-debugger.md).

![Boîte de dialogue Paramètres d’exception](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Déboguer les blocages et les conditions de concurrence

Si vous avez besoin de déboguer les genres de problèmes communs aux applications multithread, il est souvent utile d’afficher l’emplacement des threads pendant le débogage. Vous pouvez le faire facilement à l’aide du bouton **afficher les threads dans la source** .

#### <a name="to-show-threads-in-your-source-code"></a>Pour afficher les threads dans votre code source

1. Pendant le débogage, cliquez sur le bouton **afficher les threads dans la source** ![afficher les threads dans la source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dans la barre d’outils **Déboguer** .

2. Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous voyez un ![marqueur de thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") icône de *marqueur de thread* qui ressemble à deux threads en tissu. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.

    Notez qu’un marqueur de thread peut être partiellement masqué par un point d’arrêt.

3. Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu.

    Vous pouvez également afficher l’emplacement des threads dans la [fenêtre piles parallèles](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examiner les charges utiles pour les services Web et les ressources réseau (UWP)

Dans les applications UWP, vous pouvez analyser les opérations réseau effectuées à l’aide de l’API `Windows.Web.Http`. Vous pouvez utiliser cet outil pour déboguer les services Web et les ressources réseau. Pour utiliser l’outil, sélectionnez **Déboguer > profileur de performances**. Sélectionnez **réseau**, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario qui utilise `Windows.Web.Http`, puis choisissez **Arrêter la collecte** pour générer le rapport.

![Outil de profilage de l’utilisation du réseau](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Sélectionnez une opération dans la vue du résumé pour afficher des informations plus détaillées.

![Informations détaillées dans l’outil utilisation du réseau](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Pour plus d’informations, consultez [Utilisation du réseau](../profiling/network-usage.md).

## <a name="modules_window"></a>Familiarisez-vous avec la façon dont le débogueur s’attache àC#votre C++application (, F#, Visual Basic,)

Pour attacher votre application en cours d’exécution, le débogueur charge les fichiers de symboles (. pdb) générés pour la même build de l’application que vous essayez de déboguer. Dans certains scénarios, il peut être utile de disposer d’une petite connaissance des fichiers de symboles. Vous pouvez examiner la façon dont Visual Studio charge les fichiers de symboles à l’aide de la fenêtre **modules** .

Ouvrez la fenêtre **modules** pendant le débogage en sélectionnant **déboguer > modules Windows >** . La fenêtre **modules** peut vous indiquer quels sont les modules que le débogueur traite comme du code utilisateur, ou [*mon code*](../debugger/just-my-code.md), et l’état du chargement des symboles pour le module. Dans la plupart des scénarios, le débogueur recherche automatiquement des fichiers de symboles pour le code utilisateur, mais si vous souhaitez effectuer un pas à pas détaillé (ou Déboguer) du code .NET, du code système ou du code de bibliothèque tiers, des étapes supplémentaires sont nécessaires pour obtenir les fichiers de symboles appropriés.

![Afficher les informations de symboles dans la fenêtre Modules](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Vous pouvez charger les informations de symboles directement à partir de la fenêtre **modules** en cliquant avec le bouton droit et en sélectionnant **charger les symboles**.

Parfois, les développeurs d’applications livrent des applications sans les fichiers de symboles correspondants (pour réduire l’encombrement), mais conservent une copie des fichiers de symboles correspondants pour la génération afin de pouvoir déboguer ultérieurement une version publiée.

Pour savoir comment le débogueur classe le code comme du code utilisateur, consultez [uniquement mon code](../debugger/just-my-code.md). Pour en savoir plus sur les fichiers de symboles, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources dans le débogueur Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>En savoir plus

Pour obtenir des conseils et des astuces supplémentaires et des informations plus détaillées, consultez les billets de blog suivants :

- [7 piratages moins connus pour le débogage dans Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemme cachée dans Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Voir aussi

[Raccourcis clavier](../ide/productivity-shortcuts.md)
