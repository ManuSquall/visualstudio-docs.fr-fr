---
title: "GetTaskSchedulersForDebugger (m&#233;thode) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Méthode GetTaskSchedulersForDebugger, classe TaskScheduler [moteurs de débogage .NET Framework]"
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GetTaskSchedulersForDebugger (m&#233;thode)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## Valeur de retour  
 Tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives dans <xref:System.AppDomain>.  
  
## Notes  
 Cette méthode n’est pas thread\-safe et ne doit pas être utilisée en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler>. Elle doit être appelée à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.  
  
## Voir aussi  
 [Planificateur de tâches \(classe\)](../../extensibility/debugger/taskscheduler-class-internal-members.md)