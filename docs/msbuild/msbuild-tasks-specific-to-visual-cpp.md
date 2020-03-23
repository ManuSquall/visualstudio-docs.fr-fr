---
title: Tâches MSBuild Spécifiques à C Microsoft Docs
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
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633146"
---
# <a name="msbuild-tasks-specific-to-c"></a>Tâches MSBuild spécifiques à C

Les tâches fournissent le code exécuté pendant le processus de génération. Lorsque C est installé, les tâches suivantes sont disponibles, en plus de celles qui sont installées avec MSBuild. Pour plus d’informations, voir [MSBuild (C) aperçu](/cpp/build/msbuild-visual-cpp-overview).

 Outre les paramètres pour chaque tâche, chaque tâche a également les paramètres suivants.

| Paramètre | Description |
|-------------------| - |
| `Condition` | Paramètre `String` facultatif.<br /><br /> Une `Boolean` expression que le moteur MSBuild utilise pour déterminer si cette tâche sera exécutée. Pour plus d’informations sur les conditions qui sont prises en charge par MSBuild, voir [Conditions](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **vrai**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErreurAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErreurAndStop** ou **faux** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, voir [Comment : Ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[BscMake, tâche](../msbuild/bscmake-task.md)|Encapsule l’outil Microsoft Browse Information Maintenance Utility (*bscmake.exe*).|
|[Tâche CL](../msbuild/cl-task.md)|Enveloppe l’outil de compilation CMD *(cl.exe*).|
|[Tâche CPPClean](../msbuild/cppclean-task.md)|Supprime les fichiers temporaires que MSBuild crée lors de la construction d’un projet C.|
|[Tâche ClangCompile](../msbuild/clangcompile-task.md)|Enveloppe l’outil de compilation CMD *(clang.exe*).|
|[Tâche CustomBuild](../msbuild/custombuild-task.md)|Enveloppe l’outil de compilation CMD *(cmd.exe*).|
|[Tâche FXC](../msbuild/fxc-task.md)|Utilisez des compilateurs de nuanceur HLSL dans le processus de génération.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Lit les tlogs anciens, écrit les nouveaux tlogs et retourne le jeu d’éléments qui ne sont pas à jour. (tâche d’assistance)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Obtient le nom du fichier de sortie pour cl et d’autres outils, qui permet de ne spécifier que le répertoire de sortie, le nom de fichier complet, ou rien du tout. (tâche d’assistance)|
|[Tâche LIB](../msbuild/lib-task.md)|Enveloppe l’outil Microsoft 32-Bit Library Manager *(lib.exe*).|
|[Tâche de lien](../msbuild/link-task.md)|Enveloppe l’outil de liaison CMD *(link.exe*).|
|[Tâche MIDL](../msbuild/midl-task.md)|Enveloppe l’outil de compilation Microsoft Interface Definition Language (MIDL)*(midl.exe*).|
|[Tâche MT](../msbuild/mt-task.md)|Enveloppe l’outil de manifeste de Microsoft (*mt.exe*).|
|[Tâche MultiToolTask](../msbuild/multitooltask-task.md)|Aucune description.|
|[Tâche ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Exécutez des instances parallèles de la [tâche CustomBuild](../msbuild/custombuild-task.md).|
|[Tâche RC](../msbuild/rc-task.md)|Enveloppe l’outil Microsoft Windows Resource Compiler (*rc.exe*).|
|[Tâche SetEnv](../msbuild/setenv-task.md)|Définit ou supprime la valeur d’une variable d’environnement spécifiée.|
|[Classe de base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Hérite de [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Tâche VCMessage](../msbuild/vcmessage-task.md)|Enregistre les messages d’avertissement et les messages d’erreur lors de la génération. (Non extensible. Usage interne uniquement.)|
|[Classe de base VCToolTask](../msbuild/vctooltask-base-class.md)|Hérite de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake (tâche)](../msbuild/xdcmake-task.md)|Enveloppe l’outil de documentation XML (*xdcmake.exe*), qui fusionne les fichiers XML document document (*.xdc*) dans un fichier *.xml.*|
|[Tâche XSD](../msbuild/xsd-task.md)|Enveloppe l’outil XML Schema Definition (*xsd.exe*), qui génère des fichiers schémas ou de classe à partir d’une source. *Voir la remarque ci-dessous.*|
|[Référence MSBuild](../msbuild/msbuild-reference.md)|Décrit les éléments du système MSBuild.|
|[Tâches](../msbuild/msbuild-tasks.md)|Décrit des tâches, qui sont des unités de code pouvant être combinées pour produire une build.|
|[Rédaction de tâches](../msbuild/task-writing.md)|Décrit comment créer une tâche.|

> [!NOTE]
> À partir de Visual Studio 2017, *xsd.exe* n’est plus pris en charge par les projets C++. Vous pouvez toujours utiliser les API **Microsoft.VisualC.CppCodeProvider** en ajoutant manuellement *CppCodeProvider.dll* au GAC.
