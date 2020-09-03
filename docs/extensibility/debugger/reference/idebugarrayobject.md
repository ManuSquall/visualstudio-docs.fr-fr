---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736216"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface représente un objet tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour représenter un tableau.

## <a name="notes-for-callers"></a>Notes pour les appelants
 L’interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) peut obtenir cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface) si l’objet représente un tableau.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes sur l' `IDebugObject` interface, les méthodes suivantes sont implémentées sur l' `IDebugArrayObject` interface.

|Méthode|Description|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtient le nombre d’éléments dans le tableau.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtient un élément du tableau.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtient tous les éléments du tableau.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtient le rang du tableau.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtient les dimensions du tableau.|

## <a name="remarks"></a>Notes
 Un évaluateur d’expression utilise cette interface pour représenter des tableaux dans une arborescence d’analyse.

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
