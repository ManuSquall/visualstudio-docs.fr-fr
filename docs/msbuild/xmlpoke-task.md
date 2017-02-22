---
title: "XmlPoke Task | Microsoft Docs"
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
  - "XmlPoke task [MSBuild]"
  - "MSBuild, XmlPoke task"
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# XmlPoke Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit les valeurs comme spécifié par une requête XPath dans un fichier XML.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `XmlPoke`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Namespaces`|Paramètre `String` facultatif.<br /><br /> Spécifie les espaces de noms pour les préfixes de requête XPath.|  
|`Query`|Paramètre `String` facultatif.<br /><br /> Spécifie la requête XPath.|  
|`Value`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> obligatoire.<br /><br /> Spécifie le nom du fichier de sortie|  
|`XmlInputPath`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie l'entrée XML sous la forme d'un chemin d'accès de fichier.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)