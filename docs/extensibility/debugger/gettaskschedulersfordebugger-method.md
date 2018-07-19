---
title: Méthode de GetTaskSchedulersForDebugger | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5d0b78a4f115d1ba07848db914289c35034d465
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099309"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (méthode)
Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives dans <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’est pas thread-safe et ne doit pas être utilisée en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler>. Elle doit être appelée à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe du Planificateur de tâches](../../extensibility/debugger/taskscheduler-class-internal-members.md)