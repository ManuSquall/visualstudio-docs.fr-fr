---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbe3444d5bcdb31a4ef7619b123041f459a09852
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701652"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Cette interface permet à la session de débogage manager (SDM) extraire une interface qui représente le moteur de débogage (dé).

## <a name="syntax"></a>Syntaxe

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface sur les objets qui implémentent les interfaces DE courants (tels que [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), et [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) dans afin d’autoriser l’accès à la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface de la DE lui-même.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface DE type pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugQueryEngine2`.

|Méthode|Description|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtient une interface de (dé) de moteur de débogage personnalisé.|

## <a name="remarks"></a>Notes
 Cette interface est généralement implémentée dans l’objet qui implémente le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface pour prendre en charge de la causalité ordonné parcourant des fonctions ; autrement dit, lorsque le débogueur est sortir pas à une fonction, le Pour exécuter la fonction Next peut-être pas la fonction précédente sur la pile, mais une fonction dans un autre thread complètement. Pour une définition de « causalité », consultez la [glossaire du débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)