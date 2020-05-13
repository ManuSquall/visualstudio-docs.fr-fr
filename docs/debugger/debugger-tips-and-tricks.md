---
title: Conseils et astuces dans le débbugger
description: Découvrez certaines des fonctionnalités moins connues prises en charge par le plastic studio de déboulant
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
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302216"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Apprenez les conseils et astuces de productivité pour le Debugger dans Visual Studio

Lisez ce sujet pour apprendre quelques conseils et astuces de productivité pour le debugger Visual Studio. Pour un coup d’oeil aux caractéristiques de base du débbugger, voir [d’abord regarder le débbugger](../debugger/debugger-feature-tour.md). Dans ce sujet, nous couvrons certaines zones qui ne sont pas inclus dans la tournée de fonctionnalités.

## <a name="pin-data-tips"></a>Conseils de données d’épingle

Si vous vol stationnairez fréquemment sur les conseils de données tout en débogage, vous pouvez épingler la pointe de données pour la variable pour vous donner un accès rapide. La variable reste épinglée même après le redémarrage. Pour épingler la pointe des données, cliquez sur l’icône de la broche tout en planant au-dessus. Vous pouvez épingler plusieurs variables.

![Épingler un conseil de données](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modifiez votre code et continuez à débogage (C, VB, C)

Dans la plupart des langues prises en charge par Visual Studio, vous pouvez modifier votre code au milieu d’une session de débogage et continuer à débogage. Pour utiliser cette fonctionnalité, cliquez sur votre code avec votre curseur en pause dans le débogage, faites des modifications et appuyez sur **F5**, **F10**ou **F11** pour continuer à débogage.

![Modifier et continuer à débogage](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Pour plus d’informations sur l’utilisation de la fonctionnalité et sur les limitations des fonctionnalités, voir [Modifier et Continuer](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Modifier le code XAML et continuer à débogage

Pour modifier le code XAML lors d’une session de débogage, voir [Écrire et déboguer le code XAML avec XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problèmes de débbug qui sont difficiles à reproduire

S’il est difficile ou long de recréer un état particulier dans votre application, pensez si l’utilisation d’un point d’arrêt conditionnel peut aider. Vous pouvez utiliser [des points d’arrêt conditionnels](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) et des points d’arrêt de filtre pour éviter de pénétrer dans votre code d’application jusqu’à ce que l’application entre dans un état souhaité (comme un état dans lequel une variable stocke de mauvaises données). Vous pouvez définir des conditions à l’aide d’expressions, de filtres, de nombres de coups, etc.

#### <a name="to-create-a-conditional-breakpoint"></a>Créer un point d’arrêt conditionnel

1. Cliquez à droite sur une icône de point de rupture (la balle rouge) et choisissez **Conditions**.

2. Dans la fenêtre **Breakpoint Paramètres,** tapez une expression.

    ![Point d’arrêt conditionnel](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Point de rupture conditionnel")

3. Si vous êtes intéressé par un autre type d’état, sélectionnez **Filtre** au lieu de l’expression **conditionnelle** dans la boîte de dialogue **Breakpoint Paramètres,** puis suivez les conseils de filtre.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurer les données pour les afficher dans le débagé

Pour le code C, Visual Basic et CMD (code C/CLI seulement), vous pouvez indiquer au débogénaire quelles informations afficher à l’aide de l’attribut [DebuggerDisplay.](../debugger/using-the-debuggerdisplay-attribute.md) Pour le code C, vous pouvez faire de même à l’aide [de visualisations Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Changer le flux d’exécution

Avec le débbugger mis en pause sur une ligne de code, utilisez la souris pour saisir le pointeur de flèche jaune sur la gauche. Déplacez le pointeur de flèche jaune à un point différent dans le chemin d’exécution du code. Ensuite, vous utilisez F5 ou une commande d’étape pour continuer à exécuter l’application.

![Déplacer le pointeur d’exécution](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Déplacer le pointeur d’exécution")

En changeant le flux d’exécution, vous pouvez effectuer des opérations comme tester d’autres chemins d’exécution du code ou réexécuter du code sans devoir redémarrer le débogueur.

> [!WARNING]
> Vous devez rester prudent avec cette fonctionnalité, vous pouvez voir un avertissement dans l’info-bulle. Vous pouvez aussi en voir d’autres. Le déplacement du pointeur ne peut pas retourner votre application à un état d’application antérieur.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Suivre un objet hors de portée (CMD, Visual Basic)

Il est facile de voir les variables à l’aide de fenêtres débbugger comme la fenêtre **Watch.** Toutefois, lorsqu’une variable sort de portée dans la fenêtre de la **montre,** vous remarquerez peut-être qu’elle est grisée. Dans certains scénarios d’application, la valeur d’une variable peut changer même lorsque la variable est hors de portée, et vous voudrez peut-être la surveiller de près (par exemple, une variable peut obtenir des ordures collectées). Vous pouvez suivre la variable en créant un identifiant d’objet pour elle dans la fenêtre **Watch.**

#### <a name="to-create-an-object-id"></a>Pour créer un identifiant d’objet

1. Définissez un point d’arrêt près d’une variable que vous souhaitez suivre.

2. Démarrer le débbugger (**F5**) et s’arrêter au point d’arrêt.

3. Trouvez la variable dans la fenêtre **Locals** (**Debug > Windows > Locals**), cliquez à droite sur la variable, et **sélectionnez Make Object ID**.

    ![Créer un IDENTIFIANT d’objet](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Vous devriez **$** voir un plus un numéro dans la fenêtre **des sections locales.** Cette variable est l’ID de l’objet.

5. Cliquez à droite sur la variable d’identification de l’objet et choisissez **Add Watch**.

Pour plus d’informations, voir [Créer un IDENTIFIANT d’objet](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Afficher les valeurs de rendement pour les fonctions

Pour afficher les valeurs de retour pour vos fonctions, regardez les fonctions qui apparaissent dans la fenêtre **Autos** pendant que vous franchissez votre code. Pour voir la valeur de retour d’une fonction, assurez-vous que la fonction qui vous intéresse a déjà été exécutée (appuyez sur **F10** une fois si vous êtes actuellement arrêté sur l’appel de fonction). Si la fenêtre est fermée, utilisez **Debug > Windows > Autos** pour ouvrir la fenêtre **Autos.**

![Fenêtre Autos](../debugger/media/dbg-tips-autos-window.png "AutosWindow AutosWindow")

En outre, vous pouvez entrer des fonctions dans la fenêtre **immédiate** pour afficher les valeurs de retour. (Ouvrez-le à l’aide **de Debug > Windows > Immediate**.)

![Fenêtre Exécution](../debugger/media/dbg-tips-immediate-window.png "Window immediateWindow")

Vous pouvez également utiliser [des pseudovariables](../debugger/pseudovariables.md) dans `$ReturnValue`la **montre** et la fenêtre **immédiate,** tels que .

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Inspecter les cordes dans un visualiseur

Lorsque vous travaillez avec des cordes, il peut être utile de voir l’ensemble de la chaîne formatée. Pour afficher un texte simple, XML, HTML ou JSON, cliquez sur l’icône de la loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualisateur") tout en planant sur une variable contenant une valeur de chaîne.

![Ouvrez un Visualiseur à cordes](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualiseur de cordes peut vous aider à savoir si une corde est mal formée, selon le type de chaîne. Par exemple, un champ **de valeur** vierge indique que la chaîne n’est pas reconnue par le type de visualiseur. Pour plus d’informations, voir [String Visualizer Dialog Box](../debugger/string-visualizer-dialog-box.md).

![Visualisateur de cordes JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Pour quelques autres types tels que DataSet et dataTable objets qui apparaissent dans les fenêtres de déboplastage, vous pouvez également ouvrir un visualiseur intégré.

## <a name="break-into-code-on-handled-exceptions"></a>Casser le code sur les exceptions traitées

Le débbuggeur entre en panne dans votre code sur des exceptions non manipulées. Toutefois, les exceptions traitées (telles que `try/catch` les exceptions qui se produisent dans un bloc) peuvent également être une source de bogues et vous pouvez enquêter quand ils se produisent. Vous pouvez configurer le débbuggeur pour casser dans le code pour les exceptions traitées ainsi en configurant les options dans la boîte de dialogue **Des paramètres d’exception.** Ouvrez cette boîte de dialogue en choisissant **Debug > Windows > Paramètres d’exception**.

La boîte de dialogue **Des Paramètres d’Exception** vous permet de dire au débbuggeur de se casser dans le code à des exceptions spécifiques. Dans l’illustration ci-dessous, le débbuggeur se brise dans votre code chaque fois qu’un `System.NullReferenceException` se produit. Pour plus d’informations, voir [Exceptions Gérer](../debugger/managing-exceptions-with-the-debugger.md).

![Paramètres d’exception Dialog Box](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Impasses de déboiffée et conditions de course

Si vous avez besoin de déboguer les types de questions qui sont communs aux applications multithreaded, il aide souvent à afficher l’emplacement des threads tout en débogage. Vous pouvez le faire facilement en utilisant le bouton **Afficher les fils dans la source.**

#### <a name="to-show-threads-in-your-source-code"></a>Pour afficher les fils dans votre code source

1. Tout en débogage, cliquez sur les **threads Afficher dans source** le bouton ![Afficher les fils dans Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker (en)") dans la barre d’outils **Debug.**

2. Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous voyez une icône *de marqueur de fil* Thread ![Marker](../debugger/media/dbg-thread-marker.png "ThreadMarker (en)") qui ressemble à deux fils de tissu. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.

    Notez qu’un marqueur de thread peut être partiellement dissimulé par un point d’arrêt.

3. Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu.

    Vous pouvez également afficher l’emplacement des fils dans la [fenêtre Parallel Stacks](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examiner les charges utiles pour les services Web et les ressources réseau (UWP)

Dans les applications UWP, vous pouvez `Windows.Web.Http` analyser les opérations réseau effectuées à l’aide de l’API. Vous pouvez utiliser cet outil pour aider à déboiffer les services Web et les ressources réseau. Pour utiliser l’outil, sélectionnez **Debug > Performance Profiler**. Sélectionnez **Réseau**, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario qui utilise `Windows.Web.Http`, puis choisissez **Arrêter la collecte** pour générer le rapport.

![Outil de profilage d’utilisation du réseau](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Sélectionnez une opération dans la vue du résumé pour afficher des informations plus détaillées.

![Informations détaillées dans l’outil d’utilisation du réseau](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage (en anglais seulement)")

Pour plus d’informations, consultez [Utilisation du réseau](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Familiarisez-vous avec la façon dont le débbuggeur se fixe à votre application (C, CMD, Visual Basic, F)

Pour se joindre à votre application en cours d’exécution, le symbole de charge debugger (.pdb) fichiers générés pour la même version exacte de l’application que vous essayez de déboguer. Dans certains scénarios, une petite connaissance des fichiers symboles peut être utile. Vous pouvez examiner comment Visual Studio charge les fichiers symboles à l’aide de la fenêtre **Modules.**

Ouvrez la fenêtre **Modules** tout en débogage en sélectionnant **Debug > modules Windows >**. La fenêtre **Modules** peut vous indiquer quels modules le débbuggeur traite comme code utilisateur, ou [*Mon Code*](../debugger/just-my-code.md), et l’état de chargement du symbole pour le module. Dans la plupart des scénarios, le débbuggeur trouve automatiquement des fichiers symboles pour le code utilisateur, mais si vous souhaitez entrer dans (ou déboiller) .NET code, code système, ou code de bibliothèque tiers, étapes supplémentaires sont nécessaires pour obtenir les fichiers symboles corrects.

![Afficher les informations du symbole dans la fenêtre modules](../debugger/media/dbg-tips-modules-window.png "VoirSymbolInformation")

Vous pouvez charger des informations de symbole directement à partir de la fenêtre **Modules** en cliquant à droite et en choisissant **des symboles de charge**.

Parfois, les développeurs d’applications expédient des applications sans les fichiers symboles correspondants (pour réduire l’empreinte), mais conservent une copie des fichiers de symbole correspondant pour la construction afin qu’ils puissent déboiffer une version libérée plus tard.

Pour savoir comment le débogénaire classe le code comme code utilisateur, voir [Just My Code](../debugger/just-my-code.md). Pour en savoir plus sur les fichiers symboles, voir [spécifier le symbole (.pdb) et les fichiers source dans le Visual Studio debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>En savoir plus

Pour des conseils et astuces supplémentaires et des informations plus détaillées, voir ces billets de blog:

- [7 hacks moins connus pour débogage dans Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 gemmes cachées dans Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Voir aussi

[Raccourcis clavier](../ide/productivity-shortcuts.md)
