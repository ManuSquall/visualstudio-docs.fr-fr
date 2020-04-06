---
title: IDebugQueryEngine2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720654"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Cette interface permet au gestionnaire de débogé de session (SDM) de récupérer une interface qui représente le moteur de débogé (DE).

## <a name="syntax"></a>Syntaxe

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface sur les objets qui implémentent les interfaces DE les plus courantes (comme [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), et [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) afin de permettre l’accès à [l’interface IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) de la DE elle-même.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une interface DE typique pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugQueryEngine2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtient une interface personnalisée de moteur de débogé (DE).|

## <a name="remarks"></a>Notes
 Cette interface est généralement implémentée dans l’objet qui implémente [l’interface IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) afin de soutenir la causalité ordonnée en franchiant les fonctions; c’est-à-dire, lorsque le débbuggeur sort d’une fonction, la fonction suivante à exécuter peut ne pas être la fonction précédente sur la pile, mais une fonction dans un autre thread tout à fait. Pour une définition de la « causalité », voir le [Visual Studio Debugger Glossary](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
