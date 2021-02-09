---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e05cc09d2c252ddeaadc3cfa1b40e1a5797b6d79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920903"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Cette interface représente une position abstraite d’une fonction dans un document source.

## <a name="syntax"></a>Syntaxe

```
IDebugFunctionPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface pour représenter la position d’une fonction dans un document source.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est fournie dans le cadre d’une [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (plus précisément, une structure [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) ) qui fait partie intégrante de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , utilisée pour la création d’un point d’arrêt en attente.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugFunctionPosition2` .

|Méthode|Description|
|------------|-----------------|
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtient le nom de la fonction à laquelle cette position est relative.|
|[GetOffset,](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Obtient l’offset à partir du début de la fonction.|

## <a name="remarks"></a>Notes
 La position représentée par cette interface est basée sur du texte, en particulier une structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
