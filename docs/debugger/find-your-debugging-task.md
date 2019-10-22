---
title: Rechercher votre tâche de débogage
description: Identifiez la fonctionnalité du débogueur qui vous aidera à déboguer votre application
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
ms.openlocfilehash: a4667fc630d86691d95e9dc9cd205b29f7b0f525
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349706"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Rechercher votre tâche de débogage dans Visual Studio

Si vous avez besoin d’aide pour mapper votre tâche de débogage à la fonctionnalité appropriée du débogueur Visual Studio qui est pertinente, utilisez les liens fournis dans cet article. La liste des tâches comprend des tâches courantes telles que l’interruption du code pour déboguer, l’inspection des variables et l’envoi de messages à la fenêtre **sortie** . Si vous avez besoin d’une vue d’ensemble des fonctionnalités du débogueur, consultez [tout d’abord le débogueur à la](debugger-feature-tour.md) place.

## <a name="pause-running-code"></a>Suspendre le code en cours d’exécution

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Suspendre le code en cours d’exécution pour inspecter une ligne de code susceptible de contenir un bogue

Définir un point d'arrêt. Pour plus d’informations, consultez [Utilisation des points d’arrêt](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Suspendre et inspecter votre application quand elle atteint un état spécifique

Essayez un point d’arrêt conditionnel pour contrôler l’emplacement et le moment où un point d’arrêt est activé à l’aide d’une logique conditionnelle. Pour plus d’informations, consultez [conditions de point d’arrêt](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Suspendre le code uniquement lorsque la propriété ou la valeur d’un objet spécifique change

Pour C++, définissez un [point d’arrêt](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)sur variable. 
::: moniker range=">= vs-2019"
Pour les applications utilisant .NET Core 3, vous pouvez également définir un [point d’arrêt](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)sur variable.
::: moniker-end

Dans le cas C# contraire F# , pour et uniquement, vous pouvez [suivre un ID d’objet avec un point d’arrêt conditionnel](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Suspendre le code à l’intérieur d’une boucle à une certaine itération

Définissez un point d’arrêt en utilisant le **nombre d’accès** comme condition. Pour plus d’informations, consultez [nombre d’accès](using-breakpoints.md#hit-count).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Suspendre le code au début d’une fonction lorsque vous connaissez le nom de la fonction, mais pas son emplacement

Vous pouvez le faire avec un point d’arrêt sur fonction. Pour plus d’informations, consultez [définir des points d’arrêt sur fonction](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Gérer et suivre vos points d’arrêt

Utilisez la fenêtre **points d’arrêt** . Pour plus d’informations, consultez [gérer les points d’arrêt](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Suspendre le code et le débogage lorsqu’une exception gérée ou non gérée spécifique est levée

Bien que l’assistance d’exception vous indique où une erreur s’est produite, si vous souhaitez suspendre et déboguer l’erreur spécifique, vous pouvez [indiquer au débogueur de s’arrêter lorsqu’une exception est levée](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Définir un point d’arrêt à partir de la pile des appels

Si vous souhaitez suspendre et déboguer du code tout en examinant le déroulement de l’exécution ou l’affichage des fonctions dans les fenêtres **pile des appels** , consultez [définir un point d’arrêt dans la fenêtre pile des appels](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Suspendre le code au niveau d’une instruction d’assembly spécifique

Pour ce faire, vous pouvez [définir un point d’arrêt à partir de la fenêtre Code machine](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Exécuter le code

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Découvrez les commandes permettant de parcourir votre code pendant le débogage

Pour plus d’informations, consultez [naviguer dans le code avec le débogueur](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspecter des données

### <a name="check-the-value-of-variables-while-running-your-app"></a>Vérifier la valeur des variables lors de l’exécution de votre application

Pointez sur les variables à l’aide des [conseils de données](view-data-values-in-data-tips-in-the-code-editor.md) ou [Inspectez les variables dans la fenêtre automatique et variables locales](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observer la valeur modifiée d’une variable spécifique

Définissez un espion sur la variable. Pour plus d’informations, consultez [définir un espion sur les variables](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Afficher les chaînes trop longues pour la fenêtre du débogueur

Ouvrez le [visualiseur de chaîne](view-strings-visualizer.md) intégré pendant le débogage.

## <a name="configure-debugging"></a>Configurer le débogage

### <a name="customize-information-shown-in-the-debugger"></a>Personnaliser les informations affichées dans le débogueur

Vous souhaiterez peut-être afficher des informations autres que le type d’objet en tant que valeur dans différentes fenêtres du débogueur. Pour C#le code, F#Visual Basic, C++et/CLI, utilisez l’attribut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Pour obtenir des options plus avancées, vous pouvez également personnaliser l’interface utilisateur en créant un [visualiseur personnalisé](create-custom-visualizers-of-data.md).

Pour le C++mode natif, utilisez l' [infrastructure NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurer les paramètres du débogueur

Pour configurer les options de débogueur et les paramètres de projet du débogueur, consultez [paramètres et préparation du débogueur](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Tâches supplémentaires

### <a name="edit-code-during-a-debugging-session"></a>Modifier le code pendant une session de débogage

Utilisez [Modifier & Continuer](edit-and-continue.md). Pour XAML, utilisez le [rechargement à chaud XAML](xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Envoyer des messages à la fenêtre sortie sans modifier le code

Définit un trace. Pour plus d’informations, consultez Utilisation des points de [trace](using-tracepoints.md).

### <a name="debug-on-remote-machines"></a>Déboguer sur des ordinateurs distants

Consultez [Débogage à distance](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Déboguer une application qui est déjà en cours d’exécution

Consultez [attacher à un processus en cours d’exécution](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Déboguer les applications multithread

Consultez [débogage d’applications multithread](debug-multithreaded-applications-in-visual-studio.md).