---
title: "GenerateTrustInfo Task | Microsoft Docs"
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
  - "MSBuild, GenerateTrustInfo task"
  - "GenerateTrustInfo task [MSBuild]"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GenerateTrustInfo Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Génère le niveau de confiance de l'application à partir du manifeste de base, ainsi que des paramètres `TargetZone` et `ExcludedPermissions`.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `GenerateTrustInfo`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ApplicationDependencies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les assemblys dépendants.|  
|`BaseManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le manifeste de base à partir duquel le niveau de confiance de l'application doit être généré.|  
|`ExcludedPermissions`|Paramètre `String` facultatif.<br /><br /> Spécifie une ou plusieurs valeurs d'identité d'autorisation séparées par un point\-virgule à exclure du jeu d'autorisations par défaut de la zone.|  
|`TargetZone`|Paramètre `String` facultatif.<br /><br /> Spécifie un jeu d'autorisations de la zone par défaut fourni par la stratégie de l'ordinateur.|  
|`TrustInfoFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le fichier qui contient les informations d'approbation de sécurité de l'application.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)