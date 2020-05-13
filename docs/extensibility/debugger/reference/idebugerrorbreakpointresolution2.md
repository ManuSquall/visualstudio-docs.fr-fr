---
title: IDebugErrorBreakpointResolution2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d922259034d4e99c43fc06cfef8228b013fb180f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730017"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
Cette interface représente la résolution d’une erreur de point de rupture.

## <a name="syntax"></a>Syntaxe

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogé implémente cette interface dans le cadre de son support pour les points de rupture. Cette interface est utilisée pour signaler où un point d’arrêt n’a pas réussi à se lier.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) renvoie cette interface pour fournir des informations sur l’endroit où le point d’arrêt n’a pas réussi à se lier. La méthode [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) obtient l’interface [IDebugErrorBreakpoint2.](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugErrorBreakpointResolution2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtient le type de point d’arrêt.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution de point d’arrêt.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
