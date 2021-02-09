---
title: CreateProperty, tâche | Microsoft Docs
description: Utilisez la tâche MSBuild CreateProperty pour remplir les propriétés avec les valeurs passées, en autorisant la copie des valeurs d’une propriété ou d’une chaîne vers une autre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ea412f67629998eab035b8cca79111659ab8a0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901365"
---
# <a name="createproperty-task"></a>CreateProperty (tâche)

Remplit les propriétés avec les valeurs passées. Ceci permet la copie des valeurs d’une propriété ou d’une chaîne vers une autre.

## <a name="attributes"></a>Attributs

Le tableau ci-dessous décrit les paramètres de la tâche `CreateProperty` .

| Paramètre | Description |
|------------------| - |
| `Value` | Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la valeur à copier dans la nouvelle propriété. |
| `ValueSetByTask` | Paramètre de sortie `String` facultatif.<br /><br /> Contient la même valeur que le paramètre `Value`. Utilisez ce paramètre uniquement lorsque vous souhaitez éviter que la propriété de sortie ne soit définie par MSBuild quand elle ignore la cible englobante, car les sorties sont à jour. |

## <a name="remarks"></a>Remarques

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise la tâche `CreateProperty` pour créer la propriété `NewFile` en utilisant la combinaison des valeurs des propriétés `SourceFilename` et `SourceFileExtension`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Après l’exécution du projet, la valeur de la propriété `NewFile` est *Module1.vb*.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Tâches](../msbuild/msbuild-tasks.md)
