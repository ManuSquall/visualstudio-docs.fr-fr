---
title: IDebugModuleLoadEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06bb96d8a02ccc9299d43f28b4fbfa3fdb39acdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726700"
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
Cette interface est envoyée par le moteur de débogé (DE) au gestionnaire de débogé de session (SDM) lorsqu’un module est chargé ou déchargé.

## <a name="syntax"></a>Syntaxe

```
IDebugModuleLoadEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler qu’un module a été chargé ou déchargé. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler qu’un module a été chargé ou déchargé. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugModuleLoadEvent2`la méthode de .

|Méthode|Description|
|------------|-----------------|
|[GetModule (en)](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Obtient le module qui est chargé ou déchargé.|

## <a name="remarks"></a>Notes
 Visual Studio utilise cet événement pour garder la fenêtre **Modules** à jour.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
