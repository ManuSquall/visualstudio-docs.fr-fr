---
title: Méthode de SetNotificationForWaitCompletion | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a005ee7d624604dd716042bd839b48b7a367dd48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (méthode)
Active ou désactive le bit d’état TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `enabled`  
  
 `true` Pour définir le bit ; `false` à annuler le bit.  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Le débogueur définit ce bit pour aider à pas sortant d’un corps de méthode async. Si `enabled` est `true`, cette méthode doit être appelée uniquement sur une tâche qui n’est pas encore terminée. Si `enabled` est `false`, cette méthode peut être appelée sur les tâches terminées. Dans les deux cas, il ne doit être utilisé que pour les tâches de la promesse de style.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)