---
title: CallTarget, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094561"
---
# <a name="calltarget-task"></a>CallTarget (tâche)

Appelle les cibles spécifiées dans le fichier projet.

## <a name="task-parameters"></a>Paramètres de tâche

 Le tableau ci-dessous décrit les paramètres de la tâche `CallTarget` .

| Paramètre | Description |
|---------------------------| - |
| `RunEachTargetSeparately` | Paramètre d’entrée `Boolean` facultatif.<br /><br /> Si `true`, le moteur MSBuild est appelé une fois par cible. Si `false`, le moteur MSBuild est appelé une fois pour construire toutes les cibles. La valeur par défaut est `false`. |
| `TargetOutputs` | Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la sortie de toutes les cibles générées. |
| `Targets` | Paramètre `String[]` facultatif.<br /><br /> Spécifie la ou les cibles à générer. |
| `UseResultsCache` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le résultat mis en cache est retourné, le cas échéant.<br /><br /> **Remarque** Si une tâche MSBuild est exécutée, son résultat est mis en cache dans une portée (ProjectFileName, GlobalProperties)[TargetNames] sous la forme d’une liste d’éléments de build. |

## <a name="remarks"></a>Notes 

 Si une cible spécifiée dans `Targets` échoue, et si `RunEachTargetSeparately` est `true`, la tâche continue à générer les cibles restantes.

 Si vous souhaitez construire les objectifs par défaut, utilisez `Projects` la `$(MSBuildProjectFile)` [tâche MSBuild](../msbuild/msbuild-task.md) et définissez le paramètre égal à .

Lors `CallTarget`de l’utilisation , MSBuild évalue la cible appelée dans une nouvelle portée, par opposition à la même portée qu’il est appelé à partir. Cela signifie que tout élément et changement de propriété dans la cible appelée ne sont pas visibles à la cible d’appel.  Pour transmettre des informations à la `TargetOutputs` cible d’appel, utilisez le paramètre de sortie.

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour une liste de ces paramètres supplémentaires et leurs descriptions, voir [TaskExtension classe de base](../msbuild/taskextension-base-class.md).

## <a name="example"></a> Exemple

 L’exemple suivant appelle `TargetA` à partir de `CallOtherTargets`.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Cibles](../msbuild/msbuild-targets.md)
