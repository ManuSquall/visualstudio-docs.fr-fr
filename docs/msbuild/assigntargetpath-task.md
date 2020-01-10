---
title: AssignTargetPath, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a32b914cab8626df513994a3d68c2aac3d7cb7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593432"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath, tâche
Cette tâche accepte une liste de fichiers et ajoute des attributs `<TargetPath>` s’ils ne sont pas déjà spécifiés.

## <a name="task-parameters"></a>Paramètres de tâche
Le tableau ci-dessous décrit les paramètres de la tâche `AssignTargetPath` .

|Paramètre|Description|
|---------------|-----------------|
|`RootFolder`|Paramètre d’entrée `string` facultatif.<br /><br /> Contient le chemin du dossier qui contient les liens de cible.|
|`Files`|Paramètre d’entrée <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la liste de fichiers entrante.|
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` paramètre de sortie.<br /><br /> Contient la liste de fichiers résultante.|

## <a name="remarks"></a>Notes
En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple
L’exemple suivant exécute la tâche `AssignTargetPath` pour configurer un projet.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
