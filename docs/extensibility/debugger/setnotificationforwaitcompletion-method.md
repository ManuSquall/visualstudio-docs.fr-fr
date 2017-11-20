---
title: "Méthode de SetNotificationForWaitCompletion | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385ae98e90d8f3a466c0983405c367347bb8ca10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion (méthode)
Active ou désactive le bit d’état TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace :**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `enabled`  
  
 `true`Pour définir le bit ; `false` à annuler le bit.  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarques  
 Le débogueur définit ce bit pour aider à pas sortant d’un corps de méthode async. Si `enabled` est `true`, cette méthode doit être appelée uniquement sur une tâche qui n’est pas encore terminée. Si `enabled` est `false`, cette méthode peut être appelée sur les tâches terminées. Dans les deux cas, il ne doit être utilisé que pour les tâches de la promesse de style.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)