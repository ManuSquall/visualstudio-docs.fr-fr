---
title: IDebugArrayObject - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736216"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface représente un objet de tableau.

## <a name="syntax"></a>Syntaxe

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 L’évaluateur d’expression implémente cette interface pour représenter un tableau.

## <a name="notes-for-callers"></a>Notes pour les appelants
 [L’interface IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) peut obtenir cette interface en utilisant [QueryInterface](/cpp/atl/queryinterface) si l’objet représente un tableau.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes `IDebugObject` de l’interface, les `IDebugArrayObject` méthodes suivantes sont mises en œuvre sur l’interface.

|Méthode|Description|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtient le nombre d’éléments dans le tableau.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtient un élément du tableau.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtient tous les éléments du tableau.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtient le rang du tableau.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtient les dimensions du tableau.|

## <a name="remarks"></a>Notes
 Un évaluateur d’expression utilise cette interface pour représenter les tableaux dans un arbre d’analyse.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
