---
title: Méthode SetNotificationForWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 468850a441cfd0bc87155fd746d8578c6b763e66
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714385"
---
# <a name="setnotificationforwaitcompletion-method"></a>Méthode SetNotificationForWaitCompletion
Définit ou efface le bit d’état TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (dans *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Paramètres
 `enabled`

 `true` Pour définir le bit ; `false` pour le bit.

## <a name="exceptions"></a>Exceptions

## <a name="remarks"></a>Notes
 Le débogueur définit ce bit pour aider à sortir un corps de la méthode async. Si `enabled` est `true`, cette méthode doit être appelée uniquement sur une tâche qui n’est pas encore terminée. Lorsque `enabled` est `false`, cette méthode peut être appelée sur les tâches terminées. Dans les deux cas, il doit uniquement servir pour les tâches de style de promesse.

## <a name="requirements"></a>Spécifications

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)