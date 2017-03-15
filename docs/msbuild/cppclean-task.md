---
title: "CPPClean Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), CPPClean task"
  - "CPPClean task (MSBuild (Visual C++))"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# CPPClean Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Supprime les fichiers temporaires que MSBuild crée lorsqu'un projet Visual C\+\+ est construit.  Le processus de suppression des fichiers de génération est appelé *nettoyage*.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche **CPPClean** .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**DeletedFiles**|Paramètre de sortie `ITaskItem[]` facultatif.<br /><br /> Définit un tableau des éléments de fichier de sortie MSBuild qui peuvent être consommés et peuvent être émis par les tâches.|  
|**DoDelete**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, nettoie les fichiers de build temporaires.|  
|**FilePatternsToDeleteOnClean**|Paramètre `String` obligatoire.<br /><br /> Spécifie une liste délimitée par des points\-virgules d'extensions de fichiers à nettoyer.|  
|**FilesExcludedFromClean**|Paramètre `String` facultatif.<br /><br /> Spécifie une liste délimitée par des points\-virgules de fichiers à ne pas nettoyer.|  
|**FoldersToClean**|Paramètre `String` obligatoire.<br /><br /> Spécifie une liste délimitée par des points\-virgules de répertoires à nettoyer.  Vous pouvez spécifier un chemin d'accès complet ou relatif, et le chemin d'accès peut contenir le symbole générique \(**\***\).|  
  
## Notes  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)