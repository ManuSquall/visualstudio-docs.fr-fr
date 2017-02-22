---
title: "Champ TASK_STATE_FAULTED | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Champ TASK_STATE_FAULTED, la classe de tâche [moteurs de débogage .NET Framework]"
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Champ TASK_STATE_FAULTED
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Tâche terminée suite à une exception non gérée.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## Notes  
 Si le [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) champ contient cette valeur, le <xref:System.Threading.Tasks.Task.Status%2A> propriété renvoie <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)