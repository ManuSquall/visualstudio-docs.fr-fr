---
title: "Méthode de GetScheduledTasksForDebugger | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f3099cdbcc8c49c7b6cb5064efad240ea32dea4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger (méthode)
Récupère un tableau de toutes les tâches planifiées.  
  
 **Namespace :**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
 Étant donné que vous ne pouvez pas accéder à ce membre interne du .NET Framework, la syntaxe suivante est fournie en commun Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau de toutes les tâches planifiées. Chaque tâche s’exécute, ou l’exécution est terminée.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode n’est pas thread-safe et ne doit pas être utilisée en même temps que d’autres instances de <xref:System.Threading.Tasks.TaskScheduler> doit être appelée à partir d’un débogueur uniquement lorsque le débogueur a suspendu tous les autres threads.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe du Planificateur de tâches](../../extensibility/debugger/taskscheduler-class-internal-members.md)