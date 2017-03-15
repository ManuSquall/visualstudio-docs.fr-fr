---
title: "Champ TASK_STATE_WAITING_ON_CHILDREN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Champ TASK_STATE_WAITING_ON_CHILDREN, la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Champ TASK_STATE_WAITING_ON_CHILDREN
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tâche a terminé l’exécution de son délégué et attend implicitement de fin des tâches enfants attachées.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## Notes  
 Si le [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) champ contient cette valeur, le <xref:System.Threading.Tasks.Task.Status%2A> propriété renvoie <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)