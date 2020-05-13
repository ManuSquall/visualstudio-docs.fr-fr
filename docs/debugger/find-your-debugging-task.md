---
title: Rechercher votre tâche de débogage
description: Identifiez la fonction de débbugger qui vous aidera à déboiffer votre application
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302181"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Trouvez votre tâche de débogage dans Visual Studio

Si vous avez besoin d’aide pour cartographier votre tâche de débogage à la bonne caractéristique du débbuggeur Visual Studio qui est pertinent, utilisez les liens fournis dans cet article. La liste des tâches comprend ici des tâches courantes telles que la pause du code pour déboiffer, l’inspection des variables et l’envoi de messages à la fenêtre **de sortie.** Si vous avez besoin d’une vue d’ensemble des caractéristiques de débogénaire, voir [d’abord regarder le débbugger à la](debugger-feature-tour.md) place.

## <a name="pause-running-code"></a>Pause code d’exécution

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pause code d’exécution pour inspecter une ligne de code qui peut contenir un bogue

Définir un point d'arrêt. Pour plus d’informations, voir [Utiliser les points d’arrêt](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pause et inspecter votre application lorsqu’elle atteint un état spécifique

Essayez un point d’arrêt conditionnel pour contrôler où et quand un point d’arrêt est activé en utilisant la logique conditionnelle. Pour plus d’informations, voir [Conditions Breakpoint](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pause code que lorsque la propriété ou la valeur d’un objet spécifique change

Pour le C, définissez un [point d’arrêt des données](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
Pour les applications utilisant .NET Core 3, vous pouvez également définir un [point d’arrêt de données](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

Sinon, pour le C et le F seulement, vous pouvez [suivre une pièce d’identité d’objet avec un point d’arrêt conditionnel.](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f)

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pause code à l’intérieur d’une boucle à une certaine itération

Définissez un point d’arrêt en utilisant **le nombre de hit** comme condition. Pour plus d’informations, voir [Compte De coup](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pause code au début d’une fonction lorsque vous connaissez le nom de la fonction, mais pas son emplacement

Vous pouvez le faire avec un point d’arrêt de la fonction. Pour plus d’informations, voir [les points d’arrêt de la fonction Set](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Code de pause au début de plusieurs fonctions du même nom

Lorsque vous avez plusieurs fonctions du même nom (fonctions ou fonctions surchargées dans différents projets), vous pouvez utiliser un [point d’arrêt de la fonction.](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Gérez et gardez une trace de vos points d’arrêt

Utilisez la fenêtre **Breakpoints.** Pour plus d’informations, voir [Points d’arrêt Gérer](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pause code et débougeant lorsqu’une exception spécifique manipulée ou non manipulée est

Bien que l’aide d’exception vous montre où une erreur s’est produite, si vous voulez faire une pause et déboquer l’erreur spécifique, vous pouvez [dire au débbuggeur de se briser quand une exception est lancée](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Définissez un point d’arrêt à partir de la pile d’appels

Si vous souhaitez faire une pause et déboiser le code tout en examinant le flux d’exécution ou les fonctions d’affichage dans les fenêtres **Call Stack,** voir [Définir un point d’arrêt dans la fenêtre Call Stack](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Code de pause à une instruction d’assemblage spécifique

Vous pouvez le faire [en définissant un point d’arrêt de la fenêtre démontée](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Exécuter le code

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Apprenez les commandes pour passer à travers votre code tout en débogage

Pour plus d’informations, voir [Code Naviguer avec le débbugger](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspecter des données

### <a name="check-the-value-of-variables-while-running-your-app"></a>Vérifiez la valeur des variables pendant l’exécution de votre application

Survolez les variables à l’aide [de conseils de données](view-data-values-in-data-tips-in-the-code-editor.md) ou [inspectez les variables dans la fenêtre Autos and Locals.](autos-and-locals-windows.md)

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observez la valeur changeante d’une variable spécifique

Réglez une montre sur la variable. Pour plus d’informations, voir [Définir une montre sur les variables](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Afficher les chaînes qui sont trop longues pour la fenêtre de débogénaire

Ouvrez le [visualiseur de cordes](view-strings-visualizer.md) intégré tout en débogage.

## <a name="configure-debugging"></a>Configurer le débogage

### <a name="customize-information-shown-in-the-debugger"></a>Personnaliser les informations affichées dans le débagé

Vous pouvez afficher des informations autres que le type d’objet que la valeur dans différentes fenêtres de débbugger. Pour le code CMD, Visual Basic, F ET CMD/CLI, utilisez l’attribut [DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Pour des options plus avancées, vous pouvez également personnaliser l’interface utilisateur en créant un [visualiseur personnalisé.](create-custom-visualizers-of-data.md)

Pour les Cmd natifs, utilisez le [cadre NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurer les paramètres de débogénaire

Pour configurer les options de déboulant et les paramètres de projet de débogé, consultez [les paramètres et la préparation de Debugger](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Tâches supplémentaires

### <a name="fix-an-exception"></a>Fixer une exception

Voir [Fix une exception](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Modifier le code lors d’une session de débogage

Utilisez [Edit et continuer](edit-and-continue.md). Pour XAML, utilisez [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Envoyer des messages à la fenêtre de sortie sans modifier le code

Définissez un point de trace. Pour plus d’informations, voir [Utilisation des points de trace](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Afficher l’ordre dans lequel les fonctions sont appelées

Voir [comment afficher la pile d’appels](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Débogé sur des machines à distance

Consultez [Débogage à distance](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Debug une application qui est déjà en cours d’exécution

Voir [Joindre à un processus en cours d’exécution](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Déboguer les applications multithread

Voir [Les applications multithreaded Debug](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Résoudre les problèmes de performances

Voir [d’abord les outils de profilage](../profiling/profiling-feature-tour.md)