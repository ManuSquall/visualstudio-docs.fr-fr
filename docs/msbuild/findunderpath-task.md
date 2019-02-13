---
title: FindUnderPath, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bfe88fc7f31f90b6c6d4dd3935d7c40e4cc223c
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853753"
---
# <a name="findunderpath-task"></a>FindUnderPath (tâche)
Détermine quels éléments de la collection d’éléments spécifiée ont des chemins qui se trouvent dans ou sous le dossier spécifié.

## <a name="parameters"></a>Paramètres
Le tableau ci-dessous décrit les paramètres de la tâche `FindUnderPath` .

|Paramètre|Description|
|---------------|-----------------|
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers dont les chemins doivent être comparés au chemin spécifié par le paramètre `Path`.|
|`InPath`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments trouvés sous le chemin spécifié.|
|`OutOfPath`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments qui n’ont pas été trouvés sous le chemin spécifié.|
|`Path`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le chemin du dossier à utiliser comme référence.|
|`UpdateToAbsolutePaths`|Paramètre `Boolean` facultatif.<br /><br /> Si true, les chemins des éléments de sortie sont changés en chemins absolus.|

## <a name="remarks"></a>Notes
En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple
L’exemple suivant utilise la tâche `FindUnderPath` pour déterminer si les fichiers contenus dans l’élément `MyFiles` ont des chemins qui existent sous le chemin spécifié par la propriété `SearchPath`. Une fois la tâche terminée, l’élément `FilesNotFoundInPath` contient le fichier *File1.txt* et l’élément `FilesFoundInPath` contient le fichier *File2.txt*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyFiles Include="C:\File1.txt" />
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />
    </ItemGroup>

    <PropertyGroup>
        <SearchPath>C:\Projects\MyProject</SearchPath>
    </PropertyGroup>

    <Target Name="FindFiles">
        <FindUnderPath
            Files="@(MyFiles)"
            Path="$(SearchPath)">
            <Output
                TaskParameter="InPath"
                ItemName="FilesFoundInPath" />
            <Output
                TaskParameter="OutOfPath"
                ItemName="FilesNotFoundInPath" />
        </FindUnderPath>
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi
[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)  
[Tâches](../msbuild/msbuild-tasks.md)  
[Concepts MSBuild](../msbuild/msbuild-concepts.md)
