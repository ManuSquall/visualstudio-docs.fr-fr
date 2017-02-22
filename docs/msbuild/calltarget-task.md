---
title: "CallTarget Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CallTarget task [MSBuild]"
  - "MSBuild, CallTarget task"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# CallTarget Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Appelle les cibles spécifiées dans le fichier projet.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `CallTarget`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Paramètre de sortie `Boolean` facultatif.<br /><br /> Si `true`, le moteur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est appelé une fois par cible.  Si `false`, le moteur [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] est appelé une fois pour générer toutes les cibles.  La valeur par défaut est `false`.|  
|`TargetOutputs`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les sorties de toutes les cibles créées.|  
|`Targets`|Paramètre `String[]` facultatif.<br /><br /> Spécifie la ou les cibles à générer.|  
|`UseResultsCache`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, le résultat mis en cache est retourné, le cas échéant.<br /><br /> **Remarque** Lorsqu'une tâche MSBuild est exécutée, sa sortie est mise en cache dans une portée \(NomFichierProjet, PropriétésGlobales\)\[NomsCibles\] comme une liste d'éléments de génération.|  
  
## Notes  
 Si une cible spécifiée dans `Targets` échoue et que `RunEachTargetSeparately` est `true`, la tâche continue à générer les cibles restantes.  
  
 Si vous souhaitez générer les cibles par défaut, utilisez le [MSBuild, tâche](../msbuild/msbuild-task.md), avec le paramètre `Projects` égal à `$(MSBuildProjectFile)`.  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant appelle `TargetA` de l'intérieur de `CallOtherTargets`.  
  
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
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)