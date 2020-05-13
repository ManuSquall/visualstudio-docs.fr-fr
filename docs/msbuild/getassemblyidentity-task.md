---
title: GetAssemblyIdentity, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a09bd4955cee6e50368f7155fb2e03c2c1758bf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634017"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity (tâche)

Récupère les identités d’assembly des fichiers spécifiés et génère les informations d’identité.

## <a name="task-parameters"></a>Paramètres de tâche

Le tableau ci-dessous décrit les paramètres de la tâche `GetAssemblyIdentity` .

|Paramètre|Description|
|---------------|-----------------|
|`Assemblies`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les identités d’assembly récupérées.|
|`AssemblyFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les fichiers à partir desquels récupérer les identités.|

## <a name="remarks"></a>Notes 

Les éléments générés par le paramètre `Assemblies` contiennent des entrées de métadonnées d’élément nommées `Version`, `PublicKeyToken` et `Culture`.

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour une liste de ces paramètres supplémentaires et leurs descriptions, voir [TaskExtension classe de base](../msbuild/taskextension-base-class.md).

## <a name="example"></a> Exemple

L’exemple suivant récupère l’identité des fichiers spécifiés dans l’élément `MyAssemblies`, puis les génère dans l’élément `MyAssemblyIdentities`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
