---
title: Delete, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634277"
---
# <a name="delete-task"></a>Delete (tâche)

Supprime les fichiers spécifiés.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche `Delete`.

|Paramètre|Description|
|---------------|-----------------|
|`DeletedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers qui ont été supprimés.|
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers à supprimer.|
|`TreatErrorsAsWarnings`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, les erreurs sont consignées en tant qu’avertissements. La valeur par défaut est `false`.|

## <a name="remarks"></a>Notes

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Soyez prudent lorsque vous utilisez des caractères génériques avec la tâche `Delete`. Vous pouvez facilement supprimer les fichiers incorrects à l’aide d’expressions telles que `$(SomeProperty)\**\*.*` ou `$(SomeProperty)/**/*.*`, en particulier si la propriété a la valeur d’une chaîne vide, auquel cas le paramètre `Files` peut prendre la valeur de la racine de votre lecteur et être supprimé bien plus que ce que vous souhaitiez supprimer.

## <a name="example"></a>Exemple

L’exemple suivant supprime le fichier *MyApp.pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches :](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
