---
title: Méthode NotifyDebuggerOfWaitCompletion | Microsoft Docs
description: En savoir plus sur la méthode NotifyDebuggerOfWaitCompletion, qui est un espace réservé utilisé comme cible de point d’arrêt par le débogueur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606630"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Méthode NotifyDebuggerOfWaitCompletion
Méthode d’espace réservé utilisée comme cible de point d’arrêt par le débogueur. Cette méthode ne doit pas être inline ou optimisée.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (en *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Notes
 Toutes les opérations de jointure avec une tâche doivent appeler cette méthode si le bit de notification du débogueur est défini.

## <a name="requirements"></a>Configuration requise

## <a name="see-also"></a>Voir aussi
- [Classe de tâche](../../extensibility/debugger/task-class-internal-members.md)
