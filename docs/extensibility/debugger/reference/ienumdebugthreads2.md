---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6d8f869e519d9500f1ea8f3bb33a3ee098f5cfd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325416"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Cette interface énumère les threads en cours d’exécution dans la session de débogage actuelle.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter une liste de threads dans un programme.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) pour obtenir cette interface représentant une liste de tous les threads dans tous les programmes en cours d’exécution dans un processus. Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) pour obtenir cette interface représentant une liste de threads en cours d’exécution dans un programme.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugThreads2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Récupère un nombre spécifié de threads dans la séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Ignore un nombre spécifié de threads dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que celui en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtient le nombre de threads dans un énumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio obtient généralement cette interface pour mettre à jour le **Threads** fenêtre ainsi que pour obtenir le premier thread de la liste, afin d’appeler [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md), et [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
