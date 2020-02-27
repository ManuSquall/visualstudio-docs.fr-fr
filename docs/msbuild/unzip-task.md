---
title: Unzip, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Unzip
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Unzip task [MSBuild]
- MSBuild, Unzip task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d331fda05e8655be0536a1e83d8309ae8c060b1f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631508"
---
# <a name="unzip-task"></a>Tâche Unzip

Décompresse une archive *.zip* à l’emplacement spécifié.

>[!NOTE]
>La tâche `Unzip` n’est disponible qu’à partir de MSBuild 15.8.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `Unzip`.

|Paramètre|Description|
|---------------|-----------------|
|`DestinationFolder`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> obligatoire<br /><br /> Spécifie le dossier de destination dans lequel décompresser le fichier.|
|`OverwriteReadOnlyFiles`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, remplace les fichiers en lecture seule. La valeur par défaut est `false`.|
|`SkipUnchangedFiles`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, ignore la décompression des fichiers qui sont inchangés. La valeur par défaut est `true`. La tâche `Unzip` considère que les fichiers sont inchangés s’ils ont la même taille et la même heure de dernière modification.|
|`SourceFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie un ou plusieurs fichiers à décompresser. Quand vous spécifiez plusieurs fichiers, ils sont décompressés dans l’ordre dans le même dossier.|

## <a name="remarks"></a>Notes

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

 L’exemple suivant décompresse une archive et remplace tous les fichiers en lecture seule.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="UnzipArchive" BeforeTargets="Build">
        <Unzip
            SourceFiles="MyArchive.zip"
            DestinationFolder="$(OutputPath)\unzipped"
            OverwriteReadOnlyFiles="true"
        />
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches :](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
