---
title: Tâches MSBuild spécifiques à C++ | Microsoft Docs
description: Consultez les tâches MSBuild qui sont disponibles lorsque C++ est installé, que MSBuild utilise lors de la génération de code C++.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b1d1a40c9e173ec6dd7cf07e0af0ca68f58efbb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049040"
---
# <a name="msbuild-tasks-specific-to-c"></a>Tâches MSBuild spécifiques à C++

Les tâches fournissent le code exécuté pendant le processus de génération. Lorsque C++ est installé, les tâches suivantes sont disponibles, en plus de celles qui sont installées avec MSBuild. Pour plus d’informations, consultez [vue d’ensemble de MSBuild (C++)](/cpp/build/msbuild-visual-cpp-overview).

 Outre les paramètres pour chaque tâche, chaque tâche a également les paramètres suivants.

| Paramètre | Description |
|-------------------| - |
| `Condition` | Paramètre `String` facultatif.<br /><br /> `Boolean`Expression utilisée par le moteur MSBuild pour déterminer si cette tâche sera exécutée. Pour plus d’informations sur les conditions prises en charge par MSBuild, consultez [conditions](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true** . En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue** . En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (valeur par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, consultez [Comment : ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[BscMake, tâche](../msbuild/bscmake-task.md)|Encapsule l’outil Microsoft Browse Information Maintenance Utility ( *bscmake.exe* ).|
|[CL (tâche)](../msbuild/cl-task.md)|Encapsule l’outil compilateur C++ ( *cl.exe* ).|
|[CPPClean, tâche](../msbuild/cppclean-task.md)|Supprime les fichiers temporaires créés par MSBuild lors de la génération d’un projet C++.|
|[Tâche ClangCompile](../msbuild/clangcompile-task.md)|Encapsule l’outil compilateur C++ ( *clang.exe* ).|
|[Tâche CustomBuild](../msbuild/custombuild-task.md)|Encapsule l’outil compilateur C++ ( *cmd.exe* ).|
|[Tâche FXC](../msbuild/fxc-task.md)|Utilisez des compilateurs de nuanceur HLSL dans le processus de génération.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Lit les tlogs anciens, écrit les nouveaux tlogs et retourne le jeu d’éléments qui ne sont pas à jour. (tâche d’assistance)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Obtient le nom du fichier de sortie pour cl et d’autres outils, qui permet de ne spécifier que le répertoire de sortie, le nom de fichier complet, ou rien du tout. (tâche d’assistance)|
|[LIB (tâche)](../msbuild/lib-task.md)|Encapsule l’outil Gestionnaire de bibliothèques Microsoft 32 bits ( *lib.exe* ).|
|[Lier la tâche](../msbuild/link-task.md)|Encapsule l’outil C++ Linker ( *link.exe* ).|
|[MIDL (tâche)](../msbuild/midl-task.md)|Encapsule l’outil compilateur Microsoft Interface Definition Language (MIDL) ( *midl.exe* ).|
|[MT (tâche)](../msbuild/mt-task.md)|Encapsule l’outil manifeste Microsoft ( *mt.exe* ).|
|[Tâche MultiToolTask](../msbuild/multitooltask-task.md)|Pas de description.|
|[Tâche ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Exécutez des instances parallèles de la [tâche CustomBuild](../msbuild/custombuild-task.md).|
|[RC (tâche)](../msbuild/rc-task.md)|Encapsule l’outil compilateur de ressources Microsoft Windows ( *rc.exe* ).|
|[Tâche SetEnv](../msbuild/setenv-task.md)|Définit ou supprime la valeur d’une variable d’environnement spécifiée.|
|[Classe de base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Hérite de [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage (tâche)](../msbuild/vcmessage-task.md)|Enregistre les messages d’avertissement et les messages d’erreur lors de la génération. (Non extensible. Usage interne uniquement.)|
|[Classe de base VCToolTask](../msbuild/vctooltask-base-class.md)|Hérite de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake (tâche)](../msbuild/xdcmake-task.md)|Encapsule l’outil de documentation XML ( *xdcmake.exe* ), qui fusionne les fichiers de commentaires de document XML ( *. XDC* ) dans un fichier *. xml* .|
|[XSD (tâche)](../msbuild/xsd-task.md)|Encapsule l’outil XML Schema Definition ( *xsd.exe* ), qui génère des fichiers de schéma ou de classe à partir d’une source. *Voir la remarque ci-dessous.*|
|[Référence MSBuild](../msbuild/msbuild-reference.md)|Décrit les éléments du système MSBuild.|
|[Tâches](../msbuild/msbuild-tasks.md)|Décrit des tâches, qui sont des unités de code pouvant être combinées pour produire une build.|
|[Écriture de tâches](../msbuild/task-writing.md)|Décrit comment créer une tâche.|

> [!NOTE]
> À partir de Visual Studio 2017, *xsd.exe* n’est plus pris en charge par les projets C++. Vous pouvez toujours utiliser les API **Microsoft.VisualC.CppCodeProvider** en ajoutant manuellement *CppCodeProvider.dll* au GAC.
