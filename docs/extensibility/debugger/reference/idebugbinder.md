---
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdcc5e9cc87bbe97a1ff9092e34c73b72274d775
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344339"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cette interface est liée à un champ de symbole, généralement retourné par le fournisseur de symboles, à un contexte de la mémoire ou un objet qui contient la valeur actuelle du symbole.

## <a name="syntax"></a>Syntaxe

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface prend en charge l’évaluation de l’expression et doit être implémentée par le moteur de débogage (dé).

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Cette interface est utilisée dans le processus d’évaluation d’expression et est généralement utilisée dans l’implémentation de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugBinder`.

|Méthode|Description|
|------------|-----------------|
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtient le contexte de la mémoire ou d’un objet qui contient la valeur actuelle du symbole.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Détermine le type au moment de l’exécution d’un objet.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convertit une adresse mémoire ou d’emplacement de l’objet à un contexte de la mémoire.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtient un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet utilisé pour créer des paramètres de fonction.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtient le type exact d’une variable.|

## <a name="remarks"></a>Notes
 Cette interface retourne les objets qui sont utilisées par l’évaluateur d’expression en arborescences d’analyse. L’évaluateur d’expression analyse une expression en utilisant le fournisseur de symbole pour convertir les symboles dans l’expression des instances de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), qui décrivent chaque symbole en termes de son type et l’emplacement dans le code source. Le [lier](../../../extensibility/debugger/reference/idebugbinder-bind.md) méthode convertit `IDebugField` objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) les objets qui se connectent ou lier un symbole de type à une valeur réelle dans la mémoire. Ces `IDebugObject` objets sont ensuite stockées dans une arborescence d’analyse pour une évaluation ultérieure.

## <a name="requirements"></a>Configuration requise
 En-tête : ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)