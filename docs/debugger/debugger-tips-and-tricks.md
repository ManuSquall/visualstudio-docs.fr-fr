---
title: Trucs et astuces dans le débogueur Visual Studio
description: En savoir plus sur certaines des fonctionnalités connues prises en charge par le débogueur Visual Studio
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
ms.openlocfilehash: b67722884a675dd991cad608ca22cf277e2d6777
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303079"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Découvrez des conseils de productivité et des astuces pour le débogueur dans Visual Studio

Lisez cette rubrique pour découvrir quelques conseils de productivité et des conseils le débogueur Visual Studio. Pour examiner les fonctionnalités de base du débogueur, consultez [visite guidée des fonctionnalités débogueur](../debugger/debugger-feature-tour.md). Dans cette rubrique, nous abordons certaines zones qui ne sont pas inclus dans la visite guidée des fonctionnalités.

## <a name="pin-data-tips"></a>Code confidentiel des bulles d’informations

Si vous survolez fréquemment des bulles d’informations pendant le débogage, vous souhaiterez épingler la bulle pour la variable accéder rapidement. La variable reste épinglée même après le redémarrage. Pour épingler l’info-bulle de données, cliquez sur l’icône d’épingle tout en pointant dessus. Vous pouvez épingler plusieurs variables.

![L’épinglage d’une bulle](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Modifiez votre code et continuer le débogage (c#, VB, C++)

Dans la plupart des langages pris en charge par Visual Studio, vous pouvez modifier votre code au milieu d’une session de débogage et continuer le débogage. Pour utiliser cette fonctionnalité, cliquez sur dans votre code avec votre curseur pendant la suspension dans le débogueur, vérifiez les modifications, puis appuyez sur **F5**, **F10**, ou **F11** pour continuer le débogage.

![Modifier et continuer le débogage](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Pour plus d’informations sur l’utilisation de la fonctionnalité et sur les limitations de fonctionnalités, consultez [Modifier & Continuer](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Résoudre les problèmes qui sont difficiles à reproduire

S’il est difficile ou du temps recréer un état particulier dans votre application, considérez que l’utilisation d’un point d’arrêt conditionnel peut aider à. Vous pouvez utiliser [points d’arrêt conditionnels](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) et filtrer des points d’arrêt pour éviter de rompre dans votre code d’application jusqu'à ce que l’application passe à l’état souhaité (par exemple, un état dans lequel une variable stocke des données incorrectes). Vous pouvez définir des conditions à l’aide d’expressions, les filtres, les nombres d’accès et ainsi de suite.

#### <a name="to-create-a-conditional-breakpoint"></a>Pour créer un point d’arrêt conditionnel

1. Cliquez sur une icône de point d’arrêt (la balle rouge) et choisissez **Conditions**.

2. Dans le **les paramètres de point d’arrêt** fenêtre, tapez une expression.

    ![Point d’arrêt conditionnel](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Si vous êtes intéressé par un autre type de condition, sélectionnez **filtre** au lieu de **expression conditionnelle** dans le **les paramètres de point d’arrêt** boîte de dialogue, puis suivez les conseils de filtre.

## <a name="change-the-execution-flow"></a>Modifier le flux d’exécution

Avec le débogueur en pause sur une ligne de code, utilisez la souris pour obtenir le pointeur de la flèche jaune à gauche. Déplacez le pointeur de la flèche jaune vers un autre point dans le chemin d’accès de l’exécution de code. Puis vous utilisez F5 ou une commande d’étape pour poursuivre l’exécution de l’application.

![Déplacer le pointeur d’exécution](../debugger/media/dbg-tour-move-the-execution-pointer.gif "déplacer le pointeur d’exécution")

En modifiant le flux d’exécution, vous pouvez effectuer des opérations telles que les chemins d’exécution de code différent de test ou de réexécuter le code sans avoir à redémarrer le débogueur.

> [!WARNING]
> Souvent, vous devez être prudent avec cette fonctionnalité, et un avertissement s’affiche dans l’info-bulle. Vous pouvez voir les autres avertissements, trop. Déplacer le pointeur ne peut pas rétablir votre application à un état antérieur de l’application.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Suivre un objet hors de portée (c#, Visual Basic)

Il est facile d’afficher des variables à l’aide des fenêtres du débogueur, comme le **espion** fenêtre. Toutefois, quand une variable est hors de portée dans le **espion** fenêtre, vous pouvez remarquer qu’il est grisé. Dans certains scénarios d’application, la valeur d’une variable peut changer même lorsque la variable est hors de portée, et vous pouvez souhaiter surveiller de près (par exemple, une variable peut obtenir la garbage collection). Vous pouvez suivre la variable en créant un ID d’objet pour celui-ci dans le **espion** fenêtre.

#### <a name="to-create-an-object-id"></a>Pour créer un ID d’objet

1.  Définissez un point d’arrêt quasi une variable que vous souhaitez suivre.

2.  Démarrez le débogueur (**F5**) et arrêtez sur le point d’arrêt.

3. Recherchez la variable dans le **variables locales** fenêtre (**Déboguer > Windows > variables locales**), avec le bouton droit de la variable, puis sélectionnez **Make Object ID**.

    ![Créer un ID d’objet](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Le symbole **$** et un nombre s’affichent alors dans la fenêtre **Variables locales** . Cette variable est l’ID d’objet.
  
5.  Avec le bouton droit de la variable d’ID objet et choisissez **ajouter un espion**.

Pour plus d’informations, consultez [créer un ID d’objet](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Afficher les valeurs de retour pour les fonctions

Pour afficher les valeurs de retour pour vos fonctions, examinez les fonctions qui s’affichent dans le **automatique** fenêtre pendant que vous avancerez dans votre code. Pour afficher la valeur de retour pour une fonction, assurez-vous que la fonction que vous êtes intéressé a déjà été exécutée (appuyez sur **F10** une fois si vous êtes actuellement arrêté sur l’appel de fonction). Si la fenêtre est fermée, utilisez **Déboguer > Windows > automatique** pour ouvrir le **automatique** fenêtre.

![Automatique fenêtre](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

En outre, vous pouvez entrer des fonctions dans le **immédiat** fenêtre pour afficher les valeurs de retour. (Ouvrir à l’aide de **Déboguer > Windows > exécution**.)

![Fenêtre exécution](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Vous pouvez également utiliser [pseudo-variables](../debugger/pseudovariables.md) dans le **espion** et **immédiat** fenêtre, tel que `$ReturnValue`.

## <a name="string_visualizer"></a>Inspecter des chaînes dans un visualiseur

Lorsque vous travaillez avec des chaînes, il peut être utile de visualiser la totalité de la chaîne mise en forme. Pour afficher un texte brut, d’une chaîne XML, HTML ou JSON, cliquez sur l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur") tout en pointant sur une variable contenant une valeur de chaîne.

![Ouvrir un visualiseur de chaîne](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Un visualiseur de chaîne peut-être vous aider à déterminer si une chaîne est mal formée, selon le type de chaîne. Par exemple, une valeur vide **valeur** champ indique la chaîne n’est pas reconnue par le type de visualiseur. Pour plus d’informations, consultez [visualiseur de chaîne, boîte de dialogue](../debugger/string-visualizer-dialog-box.md).

![Visualiseur de chaîne JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Pour d’autres types tels que les objets WPF qui s’affichent dans les fenêtres du débogueur, vous pouvez également ouvrir des visualiseurs.

## <a name="break-into-code-on-handled-exceptions"></a>Diviser en code géré d’exceptions

Le débogueur s’arrête dans votre code sur les exceptions non gérées. Toutefois, les exceptions gérées (telles que les exceptions qui se produisent dans un `try/catch` bloc) peut également être une source de bogues et vous pouvez souhaiter examiner quand elles se produisent. Vous pouvez configurer le débogueur s’arrête dans du code pour les exceptions ainsi en configurant les options dans le **paramètres d’Exception** boîte de dialogue. Ouvrez cette boîte de dialogue en choisissant **Déboguer > Windows > Paramètres d’Exception**.

Le **paramètres d’Exception** boîte de dialogue vous permet d’indiquer le débogueur s’arrête dans du code sur des exceptions spécifiques. Dans l’illustration ci-dessous, le débogueur s’arrête dans votre code chaque fois qu’un `System.NullReferenceException` se produit. Pour plus d’informations, consultez [gestion des exceptions](../debugger/managing-exceptions-with-the-debugger.md).

![Boîte de dialogue Paramètres d’exception](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Déboguer les interblocages et conditions de concurrence

Si vous avez besoin de déboguer les types de problèmes qui sont communes aux applications multithreads, souvent vous pour permet d’afficher l’emplacement de threads pendant le débogage. Vous pouvez le faire facilement en utilisant le **afficher les Threads dans la Source** bouton.

#### <a name="to-show-threads-in-your-source-code"></a>Pour afficher les threads dans votre code source

1.  Pendant le débogage, cliquez sur le **afficher les Threads dans la Source** bouton ![afficher les Threads dans la Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dans le **déboguer** barre d’outils.
  
2.  Examinez la reliure située sur le côté gauche de la fenêtre. Sur cette ligne, vous voyez un *marqueur de thread* icône ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") qui ressemble à deux threads de maillage. Le marqueur de thread indique qu'un thread est interrompu à cet emplacement.

    Notez qu’un marqueur de thread peut être partiellement masqué par un point d’arrêt.
  
3.  Placez le pointeur sur le marqueur de thread. Un DataTip apparaît. Le DataTip vous indique le nom et le numéro d'ID de thread de chaque thread interrompu.

    Vous pouvez également afficher l’emplacement de threads dans le [fenêtre Piles parallèles](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examiner les charges utiles pour les services web et des ressources réseau (UWP)

Dans les applications UWP, vous pouvez analyser les opérations réseau effectuées à l’aide de la `Windows.Web.Http` API. Vous pouvez utiliser cet outil pour aider à déboguer des services web et des ressources réseau. Pour utiliser l’outil, sélectionnez **Déboguer > Performance Profiler**. Sélectionnez **réseau**, puis choisissez **Démarrer**. Dans votre application, effectuez le scénario qui utilise `Windows.Web.Http`, puis choisissez **Arrêter la collecte** pour générer le rapport.

![Réseau de l’utilisation de l’outil de profilage](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Sélectionnez une opération dans la vue du résumé pour afficher des informations plus détaillées.

![Informations détaillées dans l’outil de l’utilisation du réseau](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Pour plus d’informations, consultez [Utilisation du réseau](../profiling/network-usage.md).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Vous familiariser avec la façon dont le débogueur s’attache à votre application

Pour attacher à votre application en cours d’exécution, le débogueur charge les fichiers de symboles (.pdb) générés pour exactement identique à celle de l’application que vous essayez de déboguer. Dans certains scénarios, une petite base de connaissances des fichiers de symboles peut être utile. Vous pouvez examiner la façon dont Visual Studio charge les fichiers de symboles à l’aide de la **Modules** fenêtre.

Ouvrez le **Modules** fenêtre pendant le débogage en sélectionnant **Déboguer > Windows > Modules**. Le **Modules** fenêtre peut vous indiquer quels modules que le débogueur est en traitant en tant que code utilisateur, ou [ *mon Code*](../debugger/just-my-code.md)et le symbole de chargement de l’état du module. Dans la plupart des scénarios, le débogueur recherche automatiquement les fichiers de symboles pour le code utilisateur, mais si vous souhaitez pas à pas détaillé (ou debug) de code .NET framework, le code du système ou code de bibliothèque tierce, des étapes supplémentaires sont requises pour obtenir les fichiers de symbole correct.

![Afficher les informations de symbole dans la fenêtre Modules](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Vous pouvez charger les informations de symbole directement à partir de la **Modules** fenêtre en effectuant un clic droit et en choisissant **charger les symboles**.

Parfois, les développeurs d’applications livrez des applications sans les symbole fichiers correspondants (afin de réduire l’encombrement), tout en conservant une copie du symbole de correspondance de fichiers pour la build afin que pouvoir déboguer une version publiée ultérieurement.

Pour savoir comment le débogueur classe code en tant que code utilisateur, consultez [uniquement mon Code](../debugger/just-my-code.md). Pour en savoir plus sur les fichiers de symboles, consultez [spécifier les symboles (.pdb) et les fichiers sources dans le débogueur Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>En savoir plus

Pour des conseils supplémentaires et des astuces et des informations plus détaillées, consultez ces billets de blog :

- [7 piratages connus inférieure pour le débogage dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 merveilles cachées dans Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Voir aussi
[Raccourcis clavier](../ide/tips-and-tricks-for-visual-studio.md)
