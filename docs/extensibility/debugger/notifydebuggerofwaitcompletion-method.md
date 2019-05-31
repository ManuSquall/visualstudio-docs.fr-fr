---
title: Méthode NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a3280a24ad7f9d4045c9a1bff6ca2b44c724325
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350634"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Méthode NotifyDebuggerOfWaitCompletion
Méthode d’espace réservé utilisée comme cible de point d’arrêt par le débogueur. Cette méthode ne doit pas être inline ou optimisé.

 **Espace de noms :** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly :** mscorlib (dans *mscorlib.dll*)

## <a name="syntax"></a>Syntaxe

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Notes
 Toutes les opérations de jointure avec une tâche doivent appeler cette méthode si leur bit de notification de débogueur est défini.

## <a name="requirements"></a>Configuration requise

## <a name="see-also"></a>Voir aussi
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)