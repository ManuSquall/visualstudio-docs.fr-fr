---
title: IEnumDebugThreads2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715085"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Cette interface énumère les fils en cours d’exécution dans la session de débogé actuelle.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter une liste de threads dans un programme.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) pour obtenir cette interface représentant une liste de tous les threads dans tous les programmes en cours d’exécution dans un processus. Appelez [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) pour obtenir cette interface représentant une liste de threads en cours d’exécution dans un programme.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugThreads2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Récupère un nombre précis de threads dans la séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Passe un nombre spécifié de fils dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtient le nombre de fils dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio obtient généralement cette interface pour mettre à jour la fenêtre **Threads** ainsi que pour obtenir le premier thread de la liste, afin d’appeler [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md), et [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Étape](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continuer](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Exécuter](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
