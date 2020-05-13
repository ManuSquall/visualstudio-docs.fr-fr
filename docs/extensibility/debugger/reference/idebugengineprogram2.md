---
title: IDebugEngineProgram2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730302"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Cette interface fournit un support de débogage à plusieurs threads.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogé implémente cette interface pour prendre en charge le débogage simultané de plusieurs threads. Cette interface est implémentée sur le même objet qui implémente l’interface [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir `IDebugProgram2` cette interface à partir d’une interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugEngineProgram2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Arrête tous les threads en cours d’exécution dans ce programme.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Les montres pour l’exécution (ou arrêter de regarder pour l’exécution) se produisent sur le fil donné.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Permet à l’évaluation d’expression (ou de refuser) de se produire sur le thread donné, même si le programme est arrêté.|

## <a name="remarks"></a>Notes
 Visual Studio appelle cette interface en réponse à un événement [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et pour définir les états "Watch for Thread Step" et "Watch for Expression Evaluation on Thread" du programme. [L’arrêt](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelé chaque fois que le programme doit être arrêté; cette méthode donne au programme une chance de mettre fin à tous les threads.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
