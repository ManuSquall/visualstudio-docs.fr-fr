---
title: GetFrameworkPath, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65a96b59837d04deb0517d3ab79b3b668e036a20
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579639"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath (tâche)
Récupère le chemin vers les assemblys du .NET Framework.

## <a name="task-parameters"></a>Paramètres de tâche
Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkPath`.

|Paramètre|Description|
|---------------|-----------------|
|`FrameworkVersion11Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 1.1, s’ils existent. Sinon, retourne `null`.|
|`FrameworkVersion20Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 2.0, s’ils existent. Sinon, retourne `null`.|
|`FrameworkVersion30Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 3.0, s’ils existent. Sinon, retourne `null`.|
|`FrameworkVersion35Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 3.5, s’ils existent. Sinon, retourne `null`.|
|`FrameworkVersion40Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys du .NET Framework version 4.0, s’ils existent. Sinon, retourne `null`.|
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin des assemblys de la version la plus récente du .NET Framework, s’ils sont disponibles. Sinon, retourne `null`.|

## <a name="remarks"></a>Notes
Si plusieurs versions du .NET Framework sont installées, cette tâche retourne la version sur laquelle [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est conçu pour s’exécuter.

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple
L’exemple suivant utilise la tâche `GetFrameworkPath` pour stocker le chemin vers le .NET Framework dans la propriété `FrameworkPath`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi
- [Tâches :](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
