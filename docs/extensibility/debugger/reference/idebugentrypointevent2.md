---
description: Le moteur DE débogage (DE) envoie cette interface au gestionnaire de débogage de session (SDM) quand le programme est sur le point d’exécuter sa première instruction de code utilisateur.
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ccc928b3d0ca9106b6f83a4c398a694ba429ce8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065986"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Le moteur DE débogage (DE) envoie cette interface au gestionnaire de débogage de session (SDM) quand le programme est sur le point d’exécuter sa première instruction de code utilisateur.

## <a name="syntax"></a>Syntaxe

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface dans le cadre de ses opérations normales. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement lorsque le programme en cours de débogage a été chargé et est prêt à exécuter la première instruction du code utilisateur. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="remarks"></a>Notes
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) est envoyé lorsque le programme est sur le sujet d’exécuter la toute première instruction. Par exemple, `IDebugEntryPoint2` est envoyé lorsque le programme est sur le paragraphe d’exécuter la fonction de l’utilisateur `main` .

 Lors de l’envoi du `IDebugEntryPointEvent2` , la position de code actuelle doit se trouver à la première instruction du code utilisateur, comme `main` .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
