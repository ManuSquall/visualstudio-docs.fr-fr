---
title: IDebugBeforeSymbolSearchEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736113"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Le moteur de déboçon (DE) envoie cette interface au gestionnaire de déboçon de session (SDM) pour définir le message de barre d’état pendant les charges de symbole.

## <a name="syntax"></a>Syntaxe

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface lorsqu’elle doit définir le message de barre d’état pendant les charges du symbole. Cette interface n’est implémentée que par des moteurs de débogé qui fonctionnent avec ou font partie d’interprètes de script. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface (le SDM utilise **QueryInterface** pour accéder à **l’interface IDebugEvent2).**

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement lorsqu’il doit définir le message de barre d’état pendant les charges de symbole. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’elle s’est jointe au programme en cours de débbugged.

## <a name="methods"></a>Méthodes
 Le tableau suivant montre `IDebugBeforeSymbolSearchEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Récupère le nom du module actuellement en cours de débocise.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
