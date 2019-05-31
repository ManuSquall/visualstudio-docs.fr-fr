---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c500c6a54cc63dbcb8c7c6ad23c92d2105b9842
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314404"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Cette interface indique au Gestionnaire de débogage de session (SDM) qu’un saut de ligne asynchrone a été effectuée avec succès.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface pour prendre en charge les sauts de l’utilisateur dans un programme. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les appels SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) lorsque l’utilisateur a demandé le programme en cours de débogage pour être suspendu. Lorsque le programme a correctement été suspendu, l’Allemagne envoie le `IDebugBreakEvent2` événement. Cet événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="remarks"></a>Notes
 Par exemple, un utilisateur peut sélectionner la **interrompre tout** commande sur le **déboguer** menu quitter un programme qui exécute une boucle infinie. Le SDM indique au programme d’arrêter en appelant [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). L’envoie DE `IDebugBreakEvent2` lorsque le programme s’arrête enfin.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)