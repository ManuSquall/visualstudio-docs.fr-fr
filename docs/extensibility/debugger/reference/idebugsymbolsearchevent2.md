---
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85556fb8549b6ebab679fed35d5d39fbd060fbff
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703017"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Cette interface est envoyée par le moteur de débogage (dé) pour indiquer que les symboles de débogage pour un module en cours de débogage ont été chargées.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface pour signaler que les symboles d’un module ont été chargés. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler que les symboles d’un module ont été chargés. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le `IDebugSymbolSearchEvent2` interface expose la méthode suivante.

|Méthode|Description|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Récupère des informations sur les résultats d’une recherche de symbole.|

## <a name="remarks"></a>Notes
 Cet événement est envoyé même si les symboles Échec du chargement. Appel `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` permet au Gestionnaire de cet événement pour déterminer si le module a en fait tous les symboles.

 Visual Studio utilise généralement cet événement pour mettre à jour l’état des symboles chargés dans le **Modules** fenêtre.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)