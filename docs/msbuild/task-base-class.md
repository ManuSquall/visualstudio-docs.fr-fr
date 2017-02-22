---
title: "Task Base Class | Microsoft Docs"
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
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Task Base Class
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De nombreuses tâches héritent finalement de la classe <xref:Microsoft.Build.Utilities.Task>.  Cette classe ajoute plusieurs paramètres aux tâches qui en dérivent.  Ces paramètres sont énumérés dans le présent document.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de cette classe de base.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine> facultatif.<br /><br /> Spécifie l'interface du moteur de génération disponible pour les tâches.  Le moteur de génération définit automatiquement ce paramètre de manière à ce qu'il autorise les tâches à y effectuer des rappels.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine2> facultatif.<br /><br /> Spécifie l'interface du moteur de génération disponible pour les tâches.  Le moteur de génération définit automatiquement ce paramètre de manière à ce qu'il autorise les tâches à y effectuer des rappels.<br /><br /> Il s'agit d'une propriété de commodité qui évite aux auteurs de la tâche héritant de cette classe d'avoir à effectuer un cast de la valeur de `IBuildEngine` en `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine3> facultatif.<br /><br /> Spécifie l'interface du moteur de génération fournie par l'hôte.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Paramètre <xref:Microsoft.Build.Framework.ITaskHost> facultatif.<br /><br /> Spécifie l'instance d'objet hôte \(peut être null\).  Le moteur de génération définit cette propriété si l'IDE hôte a associé un objet hôte à cette tâche particulière.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Paramètre en lecture seule <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facultatif.<br /><br /> Objet d'assistance à l'enregistrement.|  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)