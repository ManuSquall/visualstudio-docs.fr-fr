---
title: FAQ - Trouver votre fonctionnalité de débogage
description: Forum aux questions (FAQ) pour vous aider à identifier la fonctionnalité du débogueur qui vous aidera à déboguer votre application
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c215b232c64b97c57285618056ee4675587b48e
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800495"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Forum aux questions : trouvez la fonctionnalité de débogage dont vous avez besoin dans Visual Studio

Si vous avez besoin d’aide pour mapper votre tâche de débogage à la fonctionnalité appropriée du débogueur Visual Studio qui est pertinente, utilisez les liens fournis dans cet article. La liste des tâches comprend des tâches courantes telles que l’interruption du code pour déboguer, l’inspection des variables et l’envoi de messages à la fenêtre **sortie** . Si vous avez besoin d’une vue d’ensemble des fonctionnalités du débogueur, consultez [tout d’abord le débogueur à la](debugger-feature-tour.md) place.

## <a name="fix-an-exception"></a>Corriger une exception

- Consultez [corriger une exception](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Suspendre le code en cours d’exécution

- **Suspendre le code en cours d’exécution pour inspecter une ligne de code susceptible de contenir un bogue**

  Définir un point d'arrêt. Pour plus d’informations, consultez [utilisation de points d’arrêt](using-breakpoints.md).

- **Suspendre et inspecter votre application quand elle atteint un état spécifique**

  Essayez un point d’arrêt conditionnel pour contrôler l’emplacement et le moment où un point d’arrêt est activé à l’aide d’une logique conditionnelle. Pour plus d’informations, consultez [conditions de point d’arrêt](using-breakpoints.md#breakpoint-conditions).

- **Suspendre le code uniquement lorsque la propriété ou la valeur d’un objet spécifique change**

  Pour C++, définissez un [point d’arrêt](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)sur variable. 
  ::: moniker range=">= vs-2019"
  Pour les applications utilisant .NET Core 3, vous pouvez également définir un [point d’arrêt](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed)sur variable.
  ::: moniker-end

  Dans le cas contraire, pour C# et F # uniquement, vous pouvez [suivre un ID d’objet avec un point d’arrêt conditionnel](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Suspendre le code à l’intérieur d’une boucle à une certaine itération**

  Définissez un point d’arrêt en utilisant le **nombre d’accès** comme condition. Pour plus d’informations, consultez [nombre d’accès](using-breakpoints.md#set-a-hit-count-condition).

- **Suspendre le code au début d’une fonction lorsque vous connaissez le nom de la fonction, mais pas son emplacement**

  Vous pouvez le faire avec un point d’arrêt sur fonction. Pour plus d’informations, consultez [définir des points d’arrêt sur fonction](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Suspendre le code au début de plusieurs fonctions portant le même nom**

  Quand vous avez plusieurs fonctions portant le même nom (fonctions ou fonctions surchargées dans différents projets), vous pouvez utiliser un [point d’arrêt sur fonction](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Gérer et suivre vos points d’arrêt**

  Utilisez la fenêtre **points d’arrêt** . Pour plus d’informations, consultez [gérer les points d’arrêt](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Suspendre le code et le débogage lorsqu’une exception gérée ou non gérée spécifique est levée**

  Bien que l’assistance d’exception vous indique où une erreur s’est produite, si vous souhaitez suspendre et déboguer l’erreur spécifique, vous pouvez [indiquer au débogueur de s’arrêter lorsqu’une exception est levée](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Définir un point d’arrêt à partir de la pile des appels**

  Si vous souhaitez suspendre et déboguer du code tout en examinant le déroulement de l’exécution ou l’affichage des fonctions dans les fenêtres **pile des appels** , consultez [définir un point d’arrêt dans la fenêtre pile des appels](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Suspendre le code au niveau d’une instruction d’assembly spécifique**

  Pour ce faire, vous pouvez [définir un point d’arrêt à partir de la fenêtre Code machine](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Exécuter le code

- **Découvrez les commandes permettant de parcourir votre code pendant le débogage**

  Pour plus d’informations, consultez [naviguer dans le code avec le débogueur](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspecter des données

- **Vérifier la valeur des variables lors de l’exécution de votre application**

  Pointez sur les variables à l’aide des [conseils de données](view-data-values-in-data-tips-in-the-code-editor.md) ou [Inspectez les variables dans la fenêtre automatique et variables locales](autos-and-locals-windows.md).

- **Observer la valeur modifiée d’une variable spécifique**

  Définissez un espion sur la variable. Pour plus d’informations, consultez [définir un espion sur les variables](watch-and-quickwatch-windows.md).

- **Afficher les chaînes trop longues pour la fenêtre du débogueur**

  Ouvrez le [visualiseur de chaîne](view-strings-visualizer.md) intégré pendant le débogage.

## <a name="debug-an-app-that-is-already-running"></a>Déboguer une application qui est déjà en cours d’exécution

- Consultez [attacher à un processus en cours d’exécution](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Déboguer les applications multithread

- Consultez [débogage d’applications multithread](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Configurer le débogage

- **Configurer les paramètres du débogueur**

  Pour configurer les options de débogueur et les paramètres de projet du débogueur, consultez [paramètres et préparation du débogueur](debugger-settings-and-preparation.md).

- **Personnaliser les informations affichées dans le débogueur**

  Vous souhaiterez peut-être afficher des informations autres que le type d’objet en tant que valeur dans différentes fenêtres du débogueur. Pour le code C#, Visual Basic, F # et C++/CLI, utilisez l’attribut [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Pour obtenir des options plus avancées, vous pouvez également personnaliser l’interface utilisateur en créant un [visualiseur personnalisé](create-custom-visualizers-of-data.md).

  Pour C++ natif, utilisez l' [infrastructure NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Tâches supplémentaires

- **Modifier le code pendant une session de débogage**

  Utilisez [Modifier & Continuer](edit-and-continue.md). Pour XAML, utilisez le [rechargement à chaud XAML](../xaml-tools/xaml-hot-reload.md).

- **Envoyer des messages à la fenêtre sortie sans modifier le code**

  Définit un trace. Pour plus d’informations, consultez Utilisation des points de [trace](using-tracepoints.md).

- **Afficher l’ordre dans lequel les fonctions sont appelées**

  Consultez [comment afficher la pile des appels](how-to-use-the-call-stack-window.md).

- **Déboguer sur des ordinateurs distants**

  Consultez [Débogage à distance](remote-debugging.md).

- **Résoudre les problèmes de performances**

  Consultez d' [abord les outils de profilage](../profiling/profiling-feature-tour.md)
