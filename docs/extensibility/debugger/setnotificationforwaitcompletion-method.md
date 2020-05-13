---
title: SetNotificationForWaitCompletion Méthode (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712874"
---
# <a name="setnotificationforwaitcompletion-method"></a>Méthode SetNotificationForWaitCompletion
Définit ou efface le TASK_STATE_WAIT_COMPLETION_NOTIFICATION’état bit.

 **Espace nom:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assemblée:** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Paramètres
 `enabled`

 `true`pour régler le bit; `false` pour décoller le bit.

## <a name="exceptions"></a>Exceptions

## <a name="remarks"></a>Notes
 Le débbugger définit ce bit pour aider à sortir d’un corps de méthode async. Si `enabled` `true`c’est le cas, cette méthode ne doit être appelée que sur une tâche qui n’a pas encore été accomplie. Quand `enabled` `false`est, cette méthode peut être appelée sur les tâches accomplies. Dans les deux cas, il ne doit être utilisé que pour des tâches de style promesse.

## <a name="requirements"></a>Spécifications

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
