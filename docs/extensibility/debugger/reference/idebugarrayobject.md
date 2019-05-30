---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be1f65e3814cbd88d32a63169234a42f76db4e6d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337583"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface représente un objet tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour représenter un tableau.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface peut obtenir cette interface à l’aide de [QueryInterface](/cpp/atl/queryinterface) si l’objet représente un tableau.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur le `IDebugObject` interface, les méthodes suivantes sont implémentées sur le `IDebugArrayObject` interface.

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
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)