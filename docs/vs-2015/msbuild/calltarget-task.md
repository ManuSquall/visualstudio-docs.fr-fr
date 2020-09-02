---
title: CallTarget, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9093b35cc444fc0b346f81a91d20afe73bd476cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160427"
---
# <a name="calltarget-task"></a>CallTarget, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Appelle les cibles spécifiées dans le fichier projet.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `CallTarget` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Paramètre de sortie `Boolean` facultatif.<br /><br /> Si `true`, le moteur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] est appelé une fois pour chaque cible. Si `false`, le moteur [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] est appelé une fois pour générer toutes les cibles. La valeur par défaut est `false`.|  
|`TargetOutputs`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient la sortie de toutes les cibles générées.|  
|`Targets`|Paramètre `String[]` facultatif.<br /><br /> Spécifie la ou les cibles à générer.|  
|`UseResultsCache`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, le résultat mis en cache est retourné, le cas échéant.<br /><br /> **Remarque** Si une tâche MSBuild est exécutée, son résultat est mis en cache dans une portée (ProjectFileName, GlobalProperties)[TargetNames] sous la forme d’une liste d’éléments de build.|  
  
## <a name="remarks"></a>Notes  
 Si une cible spécifiée dans `Targets` échoue, et si `RunEachTargetSeparately` est `true`, la tâche continue à générer les cibles restantes.  
  
 Si vous souhaitez générer les cibles par défaut, utilisez la [tâche MSBuild](../msbuild/msbuild-task.md) et définissez le paramètre `Projects` sur la valeur `$(MSBuildProjectFile)`.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle `TargetA` à partir de `CallOtherTargets`.  
  
```  
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
 [Référence de tâche](../msbuild/msbuild-task-reference.md)   
 [Cibles](../msbuild/msbuild-targets.md)
