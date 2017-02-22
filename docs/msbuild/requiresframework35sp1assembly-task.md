---
title: "RequiresFramework35SP1Assembly Task | Microsoft Docs"
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
  - "RequiresFramework35SP1Assembly task [MSBuild]"
  - "MSBuild, RequiresFramework35SP1Assembly task"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# RequiresFramework35SP1Assembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Détermine si l'application requiert .NET Framework 3.5 SP1.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `RequiresFramework35SP1Assembly`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Assemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les assemblys référencés dans l'application.|  
|`CreateDesktopShortcut`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, une icône de raccourci est créée sur le Bureau lors de l'installation.|  
|`DeploymentManifestEntryPoint`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom de fichier manifeste de l'application.|  
|`EntryPoint`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie l'assembly qui doit être exécuté lors de l'exécution de l'application.|  
|`ErrorReportUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie le site Web affiché dans les boîtes de dialogue rencontrées pendant les installations ClickOnce.|  
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie la liste des fichiers qui seront déployés lors de la publication de l'application.|  
|`ReferencedAssemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les assemblys référencés dans le projet.|  
|`RequiresMinimumFramework35SP1`|Paramètre de sortie `Boolean` facultatif.<br /><br /> Si la valeur est `true`, l'application requiert .NET Framework 3.5 SP1.|  
|`SigningManifests`|Paramètre de sortie `Boolean` facultatif.<br /><br /> Si la valeur est `true`, les manifestes ClickOnce sont signés.|  
|`SuiteName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du dossier dans le menu **Démarrer** dans lequel l'application sera installée.|  
|`TargetFrameworkVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version du .NET Framework ciblé par cette application.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)