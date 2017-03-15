---
title: "Champ TASK_STATE_EXECUTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Champ TASK_STATE_EXECUTED, la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Champ TASK_STATE_EXECUTED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tâche est en cours d’exécution mais n’est pas encore terminée.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## Notes  
 Si le [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) champ contient cette valeur, le <xref:System.Threading.Tasks.Task.Status%2A> propriété renvoie <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)