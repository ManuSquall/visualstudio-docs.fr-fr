---
title: Touch, tâche | Microsoft Docs
description: En savoir plus sur les paramètres et l’utilisation de la tâche Touch MSBuild, qui définit les heures d’accès et de modification des fichiers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dbd31edfa72368a85361032e9875b234585a07
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047007"
---
# <a name="touch-task"></a>Touch (tâche)

Définit les heures d’accès et de modification des fichiers.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `Touch` .

|Paramètre|Description|
|---------------|-----------------|
|`AlwaysCreate`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, crée tous les fichiers qui n’existent pas.|
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie la collection de fichiers à horodater.|
|`ForceTouch`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, force un horodatage de fichier même si les fichiers sont en lecture seule.|
|`Time`|Paramètre `String` facultatif.<br /><br /> Spécifie une heure autre que l’heure actuelle. Le format doit être acceptable pour la méthode <xref:System.DateTime.Parse%2A>.|
|`TouchedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la collection d’éléments horodatés.|

## <a name="remarks"></a>Remarques

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

 L’exemple suivant utilise la tâche `Touch` pour modifier les heures d’accès et de modification des fichiers spécifiés dans la collection d’éléments `Files`, et place la liste de fichiers horodatés dans la collection d’éléments `FilesTouched`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

<ItemGroup>
    <Files Include="File1.cs;File2.cs;File3.cs" />
</ItemGroup>

    <Target Name="TouchFiles">
        <Touch
            Files="@(Files)">
            <Output
                TaskParameter="TouchedFiles"
                ItemName="FilesTouched"/>
    </Touch>
</Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
