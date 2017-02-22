---
title: "Champ TASK_STATE_CANCELED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Champ TASK_STATE_CANCELED, la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Champ TASK_STATE_CANCELED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tâche a été annulée avant il atteint l’état en cours d’exécution, ou bien accepté son annulation et s’est terminée sans exception.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)  
```  
  
## Notes  
 Si le [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) champ contient cette valeur, le <xref:System.Threading.Tasks.Task.Status%2A> propriété renvoie <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)