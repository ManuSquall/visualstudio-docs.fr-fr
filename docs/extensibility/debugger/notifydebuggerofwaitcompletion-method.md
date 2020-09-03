---
title: Méthode NotifyDebuggerOfWaitCompletion | Microsoft Docs
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
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738336"
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
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
