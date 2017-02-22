---
title: "Classe TaskScheduler - membres internes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe TaskScheduler [moteurs de débogage .NET Framework]"
  - "moteurs de débogage, classe TaskScheduler (.NET Framework)"
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Classe TaskScheduler - membres internes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit les membres internes de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe qui vous aident à implémenter un débogueur personnalisé. Pour obtenir des informations générales sur cette classe, consultez la <xref:System.Threading.Tasks.TaskScheduler> rubrique de référence.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
 Étant donné que vous ne pouvez pas accéder à ces membres internes du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language \(CIL\).  
  
## Syntaxe  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## Membres  
  
### Méthodes  
  
|Nom|Description|  
|---------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Récupère un tableau de toutes les tâches planifiées.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.|  
  
## Notes  
  
## Voir aussi  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Internes de Parallel Extensions pour .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)