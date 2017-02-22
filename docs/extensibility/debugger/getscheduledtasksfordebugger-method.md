---
title: "GetScheduledTasksForDebugger (m&#233;thode) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Méthode GetScheduledTasksForDebugger, classe TaskScheduler [moteurs de débogage .NET Framework]"
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetScheduledTasksForDebugger (m&#233;thode)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un tableau de toutes les tâches planifiées.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## Valeur de retour  
 Tableau de toutes les tâches planifiées. Chaque tâche s’exécute ou est terminée.  
  
## Notes  
 Cette méthode n’est pas thread\-safe et ne doit pas être utilisée en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler> doit être appelée à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.  
  
## Voir aussi  
 [Planificateur de tâches \(classe\)](../../extensibility/debugger/taskscheduler-class-internal-members.md)