---
description: Cette interface est envoyée par le moteur de débogage (DE) au gestionnaire de débogage de session (SDM) lorsqu’un programme est attaché à.
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fb183bfc11cb3e2711d83c7cb5f18cbe908d8e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084348"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Cette interface est envoyée par le moteur de débogage (DE) au gestionnaire de débogage de session (SDM) lorsqu’un programme est attaché à.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le fournisseur DE port personnalisé implémente cette interface pour signaler qu’un programme a été créé, en général au moment où le programme est attaché. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise la `QueryInterface` méthode pour accéder à l' `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le fournisseur DE ports ou le fournisseur DE port personnalisé crée et envoie cet objet d’événement pour signaler la création d’un programme. Le DE envoie cet événement à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage. Le fournisseur de port personnalisé envoie cet événement à l’aide de l’interface [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="remarks"></a>Notes
 Le fournisseur DE ports DE ou personnalisé publie une nouvelle interface [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
