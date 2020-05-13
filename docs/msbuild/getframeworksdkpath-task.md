---
title: GetFrameworkSdkPath, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021bdb485846749ea2c7e9dfe483e09738fda46
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633991"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (tâche)

Récupère le chemin vers le kit de développement logiciel Windows (SDK).
## <a name="task-parameters"></a>Paramètres de tâche

Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkSdkPath` .
Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkSdkPath` .

|Paramètre|Description|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 2.0, s’il est présent. Sinon, retourne `String.Empty`.|
|`FrameworkSdkVersion35Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 3.5, s’il est présent. Sinon, retourne `String.Empty`.|
|`FrameworkSdkVersion40Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 4.0, s’il est présent. Sinon, retourne `String.Empty`.|
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin de la dernière version du SDK .NET, si une version est présente. Sinon, retourne `String.Empty`.|

## <a name="remarks"></a>Notes 

En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour une liste de ces paramètres supplémentaires et leurs descriptions, voir [TaskExtension classe de base](../msbuild/taskextension-base-class.md).

## <a name="example"></a> Exemple

L’exemple suivant `GetFrameworkSdkPath` utilise la tâche pour stocker le `SdkPath` chemin vers le SDK Windows dans la propriété.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
