---
title: RemoveDuplicates, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche RemoveDuplicates pour supprimer les doublons de la collection d’éléments spécifiée.
ms.custom: SEO-VS-2020
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 269499153c4be228503d6bd5b22e91e63dd5b5dd
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048675"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates (tâche)

Supprime les éléments en double de la collection d’éléments spécifiée.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `RemoveDuplicates` .

|Paramètre|Description|
|---------------|-----------------|
|`Filtered`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient une collection d’éléments dont tous les doublons ont été supprimés. L’ordre des éléments d’entrée est préservé, en conservant la première instance de chaque élément en double.|
|`Inputs`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Collection d’éléments de laquelle supprimer les éléments en double.|

## <a name="remarks"></a>Remarques

 Cette tâche ne prend pas en compte la casse et ne compare pas les métadonnées des éléments lors de la recherche des doublons.

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

 L’exemple suivant utilise la tâche `RemoveDuplicates` pour supprimer les éléments en double de la collection d’éléments `MyItems`. Lorsque la tâche est terminée, la collection d’éléments `FilteredItems` contient un élément.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 L’exemple suivant montre que la tâche `RemoveDuplicates` conserve son ordre d’entrée. Lorsque la tâche est terminée, la collection d’éléments `FilteredItems` contient les éléments *MyFile2.cs* , *MyFile1.cs* et *MyFile3.cs* dans cet ordre.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
- [Tâches](../msbuild/msbuild-tasks.md)
