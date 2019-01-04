---
title: Classe TaskScheduler - membres internes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c86b71e836c49d12c0ec0aceb3a20bf0b38e367a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853877"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - membres internes
Cet article décrit les membres internes de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe qui vous aident à implémenter un débogueur personnalisé. Pour obtenir des informations générales sur cette classe, consultez le <xref:System.Threading.Tasks.TaskScheduler> article de référence.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans *mscorlib.dll*)  
  
 Étant donné que vous ne peut pas accéder à ces membres internes à partir de .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|Nom|Description|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Récupère un tableau de toutes les tâches planifiées.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Mécanismes internes d’extension parallèle pour le .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)