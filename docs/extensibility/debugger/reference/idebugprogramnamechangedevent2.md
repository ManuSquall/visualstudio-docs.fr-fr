---
title: IDebugProgramNameChangedEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae58728601c3adbe6e37a00fd0694a5d71eef0b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722147"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Envoyé du moteur de débogé (DE) au gestionnaire de débogé de session (SDM) lorsque le nom d’un programme change.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler que le nom du programme a changé. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface **IDebugEvent2.**

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler un changement de nom de programme. Le DE envoie cet événement en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme étant débogé. Le fournisseur de port personnalisé envoie cet événement en utilisant l’interface I.

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
