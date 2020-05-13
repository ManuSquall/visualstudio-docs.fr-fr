---
title: IDebugStackFrame3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719467"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Cette interface étend [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour gérer les exceptions interceptées.

## <a name="syntax"></a>Syntaxe

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface sur le même objet qui implémente [l’interface IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour prendre en charge les exceptions interceptées.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) `IDebugStackFrame2` sur une interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expose les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gère une exception pour le cadre de pile en cours avant toute manipulation d’exception régulière.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retourne un contexte de code si une pile se détend.|

## <a name="remarks"></a>Notes
 Une exception interceptée signifie qu’un débbuggeur peut traiter une exception avant que les routines normales de manipulation des exceptions ne soient appelées par le temps d’exécution. Intercepter une exception signifie essentiellement faire le temps de course prétendre qu’il ya un gestionnaire d’exception présent, même quand il n’y a pas.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) est appelé lors de tous les événements normaux de rappel d’exception (la seule exception à cela est si vous débugging code en mode mixte (code géré et non géré), auquel cas l’exception ne peut pas être interceptée lors de la dernière chance de rappel). Si le DE ne `IDebugStackFrame3`met pas en œuvre, ou le DE renvoie une erreur de IDebugStackFrame3::`InterceptCurrentException` (comme), `E_NOTIMPL`alors le débbuggeur gérera l’exception normalement.

 En interceptant une exception, le débbuggeur peut permettre à l’utilisateur d’apporter des modifications à l’état du programme en cours de déboiffage, puis reprendre l’exécution au point où l’exception a été jetée.

> [!NOTE]
> Les exceptions interceptées ne sont autorisées que dans le code géré, c’est-à-dire dans un programme qui fonctionne sous le Common Language Runtime (CLR).

 Un moteur de déboguer indique qu’il prend en charge l’interception d’exceptions en `SetMetric` fixant des « métriques » à une valeur de 1 au moment de l’exécution en utilisant la fonction. Pour plus d’informations, voir [SDK Helpers for Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Programmes d’assistance SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
