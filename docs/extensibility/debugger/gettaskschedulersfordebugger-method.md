---
title: "Méthode de GetTaskSchedulersForDebugger | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 474d809f36d21b254dbb8bf302cd21bc83db88a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger (méthode)
Récupère un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives.  
  
 **Namespace :**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un tableau de tous les <xref:System.Threading.Tasks.TaskScheduler> les objets qui sont actuellement actives dans <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode n’est pas thread-safe et ne doit pas être utilisée en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler>. Elle doit être appelée à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe du Planificateur de tâches](../../extensibility/debugger/taskscheduler-class-internal-members.md)