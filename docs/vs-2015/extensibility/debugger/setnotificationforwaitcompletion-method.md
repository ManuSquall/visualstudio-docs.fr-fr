---
title: Méthode SetNotificationForWaitCompletion | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ea475696342808d207fc7283ee07f6d4c09e43f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734611"
---
# <a name="setnotificationforwaitcompletion-method"></a>Méthode SetNotificationForWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit ou efface le bit d’état TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly :** mscorlib (dans mscorlib.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `enabled`  
  
 `true` Pour définir le bit ; `false` pour le bit.  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Le débogueur définit ce bit pour aider à sortir un corps de la méthode async. Si `enabled` est `true`, cette méthode doit être appelée uniquement sur une tâche qui n’est pas encore terminée. Si `enabled` est `false`, cette méthode ne peut être appelée sur les tâches terminées. Dans les deux cas, il doit uniquement servir pour les tâches de style de promesse.  
  
## <a name="requirements"></a>Configuration requise  
  
## <a name="see-also"></a>Voir aussi  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)

