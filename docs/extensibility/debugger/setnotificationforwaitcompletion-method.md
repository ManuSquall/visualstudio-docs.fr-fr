---
title: Méthode SetNotificationForWaitCompletion | Microsoft Docs
description: Découvrez comment le débogueur utilise un bit d’État pour faciliter le pas à pas sortant d’un corps de méthode Async pour les tâches de style promesse.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 80904e95c1561dd20ed2a6cc9ad561e6c18ee93a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845217"
---
# <a name="setnotificationforwaitcompletion-method"></a>Méthode SetNotificationForWaitCompletion
Définit ou efface le bit d’État TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Paramètres
 `enabled`

 `true` pour définir le bit ; `false` pour annuler l’annulation du bit.

## <a name="exceptions"></a>Exceptions

## <a name="remarks"></a>Remarques
 Le débogueur définit ce bit pour faciliter le pas à pas sortant d’un corps de méthode Async. Si `enabled` est `true` , cette méthode doit être appelée uniquement sur une tâche qui n’est pas encore terminée. Lorsque `enabled` est `false` , cette méthode peut être appelée sur les tâches terminées. Dans les deux cas, il ne doit être utilisé que pour les tâches de type promesse.

## <a name="requirements"></a>Spécifications

## <a name="see-also"></a>Voir aussi
- [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
