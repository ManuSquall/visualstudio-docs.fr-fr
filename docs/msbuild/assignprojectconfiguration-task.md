---
title: Tâche AssignProjectConfiguration | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b543af39cbcd0301da7d0d353f8f7b6fa006f7ac
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508520"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration, tâche

Cette tâche accepte une liste de chaînes de configuration et les affecte aux projets spécifiés.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `AssignProjectConfiguration` .

|Paramètre|Description|
|---------------|-----------------|
|`ProjectReferences`|<xref:Microsoft.Build.Framework.ITaskItem> `[]` Paramètre d’entrée requis.<br /><br /> Projets à configurer.|
|`SolutionConfigurationContents`|Paramètre de sortie `string` facultatif.<br /><br /> Contient une chaîne XML qui contient une configuration de projet pour chaque projet. Les configurations sont affectées aux projets nommés.|
|`DefaultToVcxPlatformMapping`|Paramètre de sortie `string` facultatif.<br /><br /> Contient la liste délimitée par des points-virgules des mappages des noms de plateforme utilisés par la plupart des types à ceux utilisés par les fichiers *.vcxproj*.<br /><br /> Par exemple :<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Facultatif<br /><br /> Paramètre de sortie `string`.<br /><br /> Contient une liste délimitée par des points-virgules des mappages des noms de plateforme *. vcxproj* avec les noms de plateforme utilisés par la plupart des types.<br /><br /> Par exemple :<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Paramètre de sortie `string` facultatif.<br /><br /> Contient la configuration du projet actif.|
|`CurrentProjectPlatform`|Paramètre de sortie `string` facultatif.<br /><br /> Contient la plateforme du projet actif.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Paramètre de sortie `bool` facultatif.<br /><br /> Contient un indicateur spécifiant que des références doivent être générées même si elles ont été désactivées dans la configuration du projet.|
|`ShouldUnsetParentConfigurationAndPlatform`|Paramètre de sortie `bool` facultatif.<br /><br /> Contient un indicateur spécifiant si la définition de la plateforme et de la configuration parente doit être annulée.|
|`OutputType`|Paramètre de sortie `string` facultatif.<br /><br /> Contient le type de sortie du projet.|
|`ResolveConfigurationPlatformUsingMappings`|Paramètre de sortie `bool` facultatif.<br /><br /> Contient un indicateur spécifiant si la génération doit utiliser les mappages par défaut pour résoudre la configuration et la plateforme des éléments transmis dans les références de projet.|
|`AssignedProjects`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des chemins d’accès de référence résolus.|
|`UnassignedProjects`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste des éléments de référence de projet qui n’ont pas pu être résolus en utilisant la liste des sorties déjà résolues.|

## <a name="remarks"></a>Remarques

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
