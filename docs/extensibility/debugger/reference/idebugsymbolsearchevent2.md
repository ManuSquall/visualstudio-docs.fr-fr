---
title: IDebugSymbolSearchEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe99422e506fb86b0a7e1d9d3242783f3258e6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718787"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Cette interface est envoyée par le moteur de déboguer (DE) pour indiquer que les symboles de débogage pour un module en cours de débogage ont été chargés.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler que les symboles d’un module ont été chargés. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler que les symboles d’un module ont été chargés. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme étant débogé.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 L’interface `IDebugSymbolSearchEvent2` expose la méthode suivante.

|Méthode|Description|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Récupère des informations sur les résultats d’une recherche de symboles.|

## <a name="remarks"></a>Notes
 Cet événement sera envoyé même si les symboles n’ont pas été chargés. L’appel `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` permet au gestionnaire de cet événement de déterminer si le module a réellement des symboles.

 Visual Studio utilise généralement cet événement pour mettre à jour l’état des symboles chargés dans la fenêtre **Modules.**

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
