---
description: Cette interface représente un type d’énumération.
title: IDebugEnumField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f78e8d2560224ad22a58b74823530b6be4b1efb8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153207"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Cette interface représente un type d’énumération.

## <a name="syntax"></a>Syntaxe

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de symboles implémente cette interface pour représenter une énumération.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface à partir de l’interface [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) retourne `FIELD_TYPE_ENUM` .

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre VTable
 Outre les méthodes sur les `IDebugField` `IDebugContainerField` interfaces et, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Retourne un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) décrivant le nom de ce type d’énumération.|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Retourne le nom de la constante d’énumération associée à la valeur donnée.|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Retourne la valeur associée au nom de la constante d’énumération donnée|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Retourne la valeur associée au nom de la constante d’énumération donnée, mais qui ignore la casse.|

## <a name="remarks"></a>Notes
 Il s’agit du symbole sous-jacent qui est réellement lié à un emplacement avec [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces des fournisseurs de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Établis](../../../extensibility/debugger/reference/idebugbinder-bind.md)
