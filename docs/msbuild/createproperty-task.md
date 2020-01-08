---
title: CreateProperty, tâche | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cac0af3371a5c4ae385cc19367b360b8e8f608fd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590057"
---
# <a name="createproperty-task"></a>CreateProperty (tâche)
Remplit les propriétés avec les valeurs passées. Ceci permet la copie des valeurs d’une propriété ou d’une chaîne vers une autre.

## <a name="attributes"></a>Attributs
Le tableau ci-dessous décrit les paramètres de la tâche `CreateProperty` .

| Paramètre | Description |
|------------------| - |
| `Value` | Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la valeur à copier dans la nouvelle propriété. |
| `ValueSetByTask` | Paramètre de sortie `String` facultatif.<br /><br /> Contient la même valeur que le paramètre `Value`. Utilisez ce paramètre seulement quand vous voulez éviter que la propriété de sortie soit définie par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] quand il ignore la cible englobante en raison du fait que les sorties sont à jour. |

## <a name="remarks"></a>Notes
En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

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
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
