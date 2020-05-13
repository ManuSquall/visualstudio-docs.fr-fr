---
title: IDebugBinder - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735973"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Cette interface lie un champ de symbole, généralement retourné par le fournisseur de symboles, à un contexte de mémoire ou un objet qui contient la valeur actuelle du symbole.

## <a name="syntax"></a>Syntaxe

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface prend en charge l’évaluation de l’expression et doit être mise en œuvre par le moteur de débogé (DE).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est utilisée dans le processus d’évaluation de l’expression et est généralement utilisée dans la mise en œuvre de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugBinder`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtient le contexte de mémoire ou l’objet qui contient la valeur actuelle du symbole.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Détermine le type d’objet en temps de course.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convertit un emplacement d’objet ou une adresse mémoire en contexte de mémoire.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtient un objet [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) utilisé pour créer des paramètres de fonction.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtient le type exact pour une variable.|

## <a name="remarks"></a>Notes
 Cette interface renvoie les objets qui sont utilisés par l’évaluateur d’expression dans les arbres d’analyse. L’évaluateur d’expression analyse une expression en utilisant le fournisseur de symboles pour convertir les symboles dans l’expression en cas [d’IDebugField](../../../extensibility/debugger/reference/idebugfield.md), qui décrivent chaque symbole en termes de son type et de son emplacement dans le code source. La [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) méthode Bind `IDebugField` convertit les objets en objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui relient ou lient un type de symbole à une valeur réelle de la mémoire. Ces `IDebugObject` objets sont ensuite stockés dans un arbre d’analyse pour une évaluation ultérieure.

## <a name="requirements"></a>Spécifications
 En-tête: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces d’évaluation des expressions](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
