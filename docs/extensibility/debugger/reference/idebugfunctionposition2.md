---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19b9fbe16abec97ef29794b66cc4fe92631ca0af
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313251"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Cette interface représente une position abstraite d’une fonction dans un document source.

## <a name="syntax"></a>Syntaxe

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter la position d’une fonction au sein d’un document source.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface est fournie en tant que partie d’un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (plus précisément, un [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) structure) qui est à son tour de partie de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure, utilisée lors de la création d’un point d’arrêt en attente.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugFunctionPosition2`.

|Méthode|Description|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtient le nom de la fonction de cette position est relative.|
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Obtient le décalage à partir du début de la fonction.|

## <a name="remarks"></a>Notes
 La position représentée par cette interface est basée sur le texte, en particulier, un [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)