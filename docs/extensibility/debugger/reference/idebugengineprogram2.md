---
description: Cette interface offre une prise en charge du débogage multithread.
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e52ae6477b49325d4b8a4d81192fe2ecf736163
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092655"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Cette interface offre une prise en charge du débogage multithread.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogage implémente cette interface pour prendre en charge le débogage simultané de plusieurs threads. Cette interface est implémentée sur le même objet qui implémente l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir d’une `IDebugProgram2` interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEngineProgram2` .

|Méthode|Description|
|------------|-----------------|
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arrête tous les threads qui s’exécutent dans ce programme.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Surveille l’exécution (ou l’arrêt de la surveillance de l’exécution) sur le thread donné.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Autorise (ou interdit) l’évaluation d’une expression sur le thread donné, même si le programme est arrêté.|

## <a name="remarks"></a>Notes
 Visual Studio appelle cette interface en réponse à un événement [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et définit les États « surveiller les threads » et « surveiller l’évaluation des expressions sur le thread » du programme. L' [arrêt](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelé chaque fois que le programme doit être arrêté. Cette méthode donne au programme la possibilité d’arrêter tous les threads.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
