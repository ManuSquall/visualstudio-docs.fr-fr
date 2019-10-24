---
title: Tâches MSBuild spécifiques à C++ | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d6ea400d7473fae27ac4b17d9e3692748db549f3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748074"
---
# <a name="msbuild-tasks-specific-to-c"></a>Tâches MSBuild spécifiques àC++
Les tâches fournissent le code exécuté pendant le processus de génération. Lorsque C++ est installé, les tâches suivantes sont disponibles, en plus de celles qui sont installées avec [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pour plus d’informations, consultez [vueC++d’ensemble de MSBuild ()](/cpp/build/msbuild-visual-cpp-overview).

 Outre les paramètres pour chaque tâche, chaque tâche a également les paramètres suivants.

| Paramètre | Description |
|-------------------| - |
| `Condition` | Paramètre `String` facultatif.<br /><br /> Expression `Boolean` utilisée par le moteur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pour déterminer si cette tâche va être exécutée. Pour plus d’informations sur les conditions prises en charge par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consultez [Conditions](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Paramètre facultatif. Peut contenir l’une des valeurs suivantes :<br /><br /> -   **WarnAndContinue** ou **true**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément [Target](../msbuild/target-element-msbuild.md) et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des avertissements.<br />-   **ErrorAndContinue**. En cas d’échec d’une tâche, l’exécution des tâches suivantes de l’élément `Target` et de la génération se poursuit, et toutes les erreurs de la tâche sont considérées comme des erreurs.<br />-   **ErrorAndStop** ou **false** (par défaut). En cas d’échec d’une tâche, les tâches restantes de l’élément `Target` et de la génération ne sont pas exécutées, et tout l’élément `Target` ainsi que la génération sont considérés comme étant en échec.<br /><br /> Les versions de .NET Framework antérieures à 4.5 prenaient en charge uniquement les valeurs `true` et `false`.<br /><br /> Pour plus d’informations, voir [Guide pratique : Ignorer les erreurs dans les tâches](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Tâche BscMake](../msbuild/bscmake-task.md)|Encapsule l’outil Microsoft Browse Information Maintenance Utility (*bscmake.exe*).|
|[Tâche CL](../msbuild/cl-task.md)|Encapsule l' C++ outil compilateur (*CL. exe*).|
|[Tâche CPPClean](../msbuild/cppclean-task.md)|Supprime les fichiers temporaires créés par MSBuild lorsqu’un C++ projet est généré.|
|[Tâche ClangCompile](../msbuild/clangcompile-task.md)|Encapsule l' C++ outil compilateur (*Clang. exe*).|
|[Tâche CustomBuild](../msbuild/custombuild-task.md)|Encapsule l' C++ outil compilateur (*cmd. exe*).|
|[Tâche FXC](../msbuild/fxc-task.md)|Utilisez des compilateurs de nuanceur HLSL dans le processus de génération.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Lit les tlogs anciens, écrit les nouveaux tlogs et retourne le jeu d’éléments qui ne sont pas à jour. (tâche d’assistance)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Obtient le nom du fichier de sortie pour cl et d’autres outils, qui permet de ne spécifier que le répertoire de sortie, le nom de fichier complet, ou rien du tout. (tâche d’assistance)|
|[Tâche LIB](../msbuild/lib-task.md)|Inclut l’outil Gestionnaire de bibliothèques 32 bits de Microsoft (*lib.exe*) dans un wrapper.|
|[Tâche Link](../msbuild/link-task.md)|Encapsule l' C++ outil Éditeur de liens (*Link. exe*).|
|[Tâche MIDL](../msbuild/midl-task.md)|Inclut l’outil Compilateur MIDL (Microsoft Interface Definition Language) (*midl.exe*) dans un wrapper.|
|[Tâche MT](../msbuild/mt-task.md)|Inclut l’outil Manifeste de Microsoft (*mt.exe*) dans un wrapper.|
|[Tâche MultiToolTask](../msbuild/multitooltask-task.md)|Aucune description.|
|[Tâche ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Exécutez des instances parallèles de la [tâche CustomBuild](../msbuild/custombuild-task.md).|
|[Tâche RC](../msbuild/rc-task.md)|Inclut l’outil Compilateur de ressources Microsoft Windows (*rc.exe*) dans un wrapper.|
|[Tâche SetEnv](../msbuild/setenv-task.md)|Définit ou supprime la valeur d’une variable d’environnement spécifiée.|
|[Classe de base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Hérite de [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[Tâche VCMessage](../msbuild/vcmessage-task.md)|Enregistre les messages d’avertissement et les messages d’erreur lors de la génération. (Non extensible. Usage interne uniquement.)|
|[Classe de base VCToolTask](../msbuild/vctooltask-base-class.md)|Hérite de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[Tâche XDCMake](../msbuild/xdcmake-task.md)|Inclut dans un wrapper l’outil Documentation XML (*xdcmake.exe*), qui fusionne des fichiers de commentaires documentation XML ( *.xdc*) dans un fichier *.xml*.|
|[Tâche XSD](../msbuild/xsd-task.md)|Inclut dans un wrapper l’outil Définition de schéma XML (*xsd.exe*), qui génère des fichiers de schéma ou de classe à partir d’une source. *Voir la remarque ci-dessous.*|
|[Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)|Décrit les éléments du système MSBuild.|
|[Tâches MSBuild](../msbuild/msbuild-tasks.md)|Décrit des tâches, qui sont des unités de code pouvant être combinées pour produire une build.|
|[Écriture de tâches](../msbuild/task-writing.md)|Décrit comment créer une tâche.|

> [!NOTE]
> À partir de Visual Studio 2017, *xsd.exe* n’est plus pris en charge par les projets C++. Vous pouvez toujours utiliser les API **Microsoft.VisualC.CppCodeProvider** en ajoutant manuellement *CppCodeProvider.dll* au GAC.