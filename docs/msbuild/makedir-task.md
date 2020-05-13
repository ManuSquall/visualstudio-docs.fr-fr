---
title: MakeDir, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cc2e97a3024d768861a1967705137415a0d3aa2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633536"
---
# <a name="makedir-task"></a>MakeDir (tâche)

Crée des répertoires et, si nécessaire, des répertoires parents.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `MakeDir` .

|Paramètre|Description|
|---------------|-----------------|
|`Directories`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Ensemble de répertoires à créer.|
|`DirectoriesCreated`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Répertoires créés par cette tâche. Si des répertoires n’ont pas pu être créés, certains des éléments passés au paramètre `Directories` peuvent manquer.|

## <a name="remarks"></a>Notes 

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour une liste de ces paramètres supplémentaires et leurs descriptions, voir [TaskExtension classe de base](../msbuild/taskextension-base-class.md).

## <a name="example"></a> Exemple

L’exemple de code suivant utilise la tâche `MakeDir` pour créer le répertoire spécifié par la propriété `OutputDirectory`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
    </PropertyGroup>

    <Target Name="CreateDirectories">
        <MakeDir
            Directories="$(OutputDirectory)"/>
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
