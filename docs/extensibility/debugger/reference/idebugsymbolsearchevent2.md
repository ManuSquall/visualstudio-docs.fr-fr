---
description: Cette interface est envoyée par le moteur de débogage (DE) pour indiquer que les symboles de débogage d’un module en cours de débogage ont été chargés.
title: IDebugSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a4ef5008740f563f2f7f986f73c8bbfbb94ef6b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053137"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Cette interface est envoyée par le moteur de débogage (DE) pour indiquer que les symboles de débogage d’un module en cours de débogage ont été chargés.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler que les symboles d’un module ont été chargés. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler que les symboles d’un module ont été chargés. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 L' `IDebugSymbolSearchEvent2` interface expose la méthode suivante.

|Méthode|Description|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Récupère des informations sur les résultats d’une recherche de symboles.|

## <a name="remarks"></a>Notes
 Cet événement est envoyé même en cas d’échec du chargement des symboles. `IDebugSymbolSearchEvent2::GetSymbolSearchInfo`L’appel à permet au gestionnaire de cet événement de déterminer si le module a en fait des symboles.

 Visual Studio utilise généralement cet événement pour mettre à jour l’état des symboles chargés dans la fenêtre **modules** .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
