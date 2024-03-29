---
description: Cette interface permet au gestionnaire de débogage de session (SDM) de récupérer une interface qui représente le moteur DE débogage (DE).
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 899c5dceab16d4783cb28bff31c67e67bf5df774
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083646"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Cette interface permet au gestionnaire de débogage de session (SDM) de récupérer une interface qui représente le moteur DE débogage (DE).

## <a name="syntax"></a>Syntaxe

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface sur les objets qui implémentent les interfaces DE la plus courante (telles que [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)et [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) afin d’autoriser l’accès à l’interface [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) de la classe.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface de type standard pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugQueryEngine2` .

|Méthode|Description|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtient une interface DE moteur DE débogage personnalisé (DE).|

## <a name="remarks"></a>Notes
 Cette interface est généralement implémentée dans l’objet qui implémente l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) afin de prendre en charge l’exécution pas à pas de la causalité dans les fonctions ; autrement dit, lorsque le débogueur effectue un pas à pas sortant d’une fonction, la fonction suivante à exécuter peut ne pas être la fonction précédente sur la pile, mais une fonction dans un autre thread. Pour une définition de « causalité », consultez le [Glossaire du débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
