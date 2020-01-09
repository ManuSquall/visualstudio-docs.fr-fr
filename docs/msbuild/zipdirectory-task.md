---
title: ZipDirectory, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4bf72509610e9d397e4b208294112fcc0975b4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588328"
---
# <a name="zipdirectory-task"></a>Tâche ZipDirectory
Crée une archive *.zip* à partir du contenu d’un répertoire.

>[!NOTE]
>La tâche `ZipDirectory` n’est disponible qu’à partir de MSBuild 15.8.

## <a name="parameters"></a>Parameters
 Le tableau ci-dessous décrit les paramètres de la tâche `ZipDirectory` .

|Paramètre|Description|
|---------------|-----------------|
|`DestinationFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> obligatoire<br /><br /> Chemin d’accès complet du fichier *.zip* à créer.|
|`Overwrite`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, le fichier de destination est remplacé s’il existe. La valeur par défaut est `false`.|
|`SourceDirectory`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le répertoire à partir duquel sera créée une archive *.zip*.|

## <a name="remarks"></a>Notes
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple
 L’exemple suivant crée une archive *.zip* à partir du répertoire de sortie après la génération d’un projet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
