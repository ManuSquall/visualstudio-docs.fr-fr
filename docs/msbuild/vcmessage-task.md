---
title: "VCMessage Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "VCMessage task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), VCMessage task"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# VCMessage Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enregistre les messages d'erreur et d'avertissement pendant une génération.  
  
## Notes  
 Cette tâche aide à implémenter MSBuild pour Visual C\+\+ et n'est pas censée être appelée par l'utilisateur.  Pour plus d'informations, consultez <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche **VCMessage** .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Arguments**|Paramètre **String** facultatif.<br /><br /> Une liste délimitée par des points\-virgules de messages à afficher.|  
|**Code**|Paramètre **String** obligatoire.<br /><br /> Numéro d'erreur qui qualifie le message.|  
|**Type**|Paramètre **String** facultatif.<br /><br /> Spécifie le type de message à émettre.  Spécifiez `"Avertissement"` pour émettre un message d'avertissement ou `"Erreur"` pour émettre un message d'erreur.|  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)