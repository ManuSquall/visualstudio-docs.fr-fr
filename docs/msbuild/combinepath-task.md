---
title: CombinePath, tâche | Microsoft Docs
description: Découvrez comment utiliser la tâche CombinePath MSBuild pour combiner les chemins d’accès spécifiés en un seul chemin d’accès.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1eb27a311f1b61e3e36b4c9eaa65de7f3fd8f1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939498"
---
# <a name="combinepath-task"></a>CombinePath (tâche)

Combine les chemins spécifiés en un chemin unique.
## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche [CombinePath](../msbuild/combinepath-task.md).


|Paramètre|Description|
|---------------|-----------------|
|`BasePath`|Paramètre `String` requis.<br /><br /> Chemin de base à combiner aux autres chemins. Peut être un chemin relatif, absolu ou vide.|
|`Paths`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste de chemins individuels à combiner avec BasePath pour former le chemin combiné. Les chemins peuvent être relatifs ou absolus.|
|`CombinedPaths`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Chemin combiné créé par cette tâche.|

## <a name="remarks"></a>Notes

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

 L’exemple suivant montre comment créer une structure de dossier de sortie à l’aide `CombinePath` de pour construire la propriété `$(OutputDirectory)` en combinant un chemin d’accès racine `$(PublishRoot)` concaténé avec `$(ReleaseDirectory)` et une liste de sous-dossiers `$(LangDirectories)` .

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

La seule propriété qui `CombinePath` autorise à être une liste est `Paths` , auquel cas la sortie est également une liste. Ainsi, si `$(PublishRoot)` est *C:\Site1 \\* et `$(ReleaseDirectory)` est *Release \\* et `@(LangDirectories)` est *en-US \; fr-fr \\*, cet exemple crée les dossiers :

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
