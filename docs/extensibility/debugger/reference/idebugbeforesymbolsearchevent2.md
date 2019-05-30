---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83e71b6059f19840311075261940942010f2e99e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349556"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Le moteur de débogage (dé) envoie cette interface pour le Gestionnaire de débogage (SDM) pour définir l’état de session à la barre de message au cours des charges de symbole.

## <a name="syntax"></a>Syntaxe

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface lorsqu’elle doit définir le message de barre d’état au cours des charges de symbole. Cette interface est implémentée uniquement par les moteurs de débogage qui fonctionnent ou qui font partie des interpréteurs de script. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface (utilise le SDM **QueryInterface** pour accéder à la **IDebugEvent2** interface).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement quand il doit définir le message de barre d’état au cours des charges de symbole. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugBeforeSymbolSearchEvent2`.

|Méthode|Description|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Récupère le nom du module en cours de débogage.|

## <a name="requirements"></a>Configuration requise
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll