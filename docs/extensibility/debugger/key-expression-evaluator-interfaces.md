---
title: Interfaces d’évaluateur d’expression clés (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738490"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces d’évaluateur d’expression clés
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Lors de la rédaction d’un évaluateur d’expression (EE), ainsi que le contexte d’évaluation, vous devez être familier avec les interfaces suivantes.

## <a name="interface-descriptions"></a>Descriptions d’interface

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     A une seule méthode, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), qui obtient une structure de données qui représente le point d’exécution actuel. Cette structure de données est l’un des trois arguments que le moteur de débogé (DE) passe à la méthode [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour évaluer une expression. Cette interface est généralement implémentée par le fournisseur de symboles.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     A la méthode [Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) qui obtient la zone de mémoire qui contient la valeur actuelle d’un symbole. Compte tenu à la fois de la méthode de confinement, représentée par un objet [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) et du symbole lui-même, représenté par un objet [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) `IDebugBinder::Bind` retourne la valeur du symbole. `IDebugBinder`est généralement mis en œuvre par le DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Représente un type de données simple. Pour les types plus complexes, tels que les tableaux et les méthodes, utilisez les interfaces [dérivées IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) et [IDebugMethodField,](../../extensibility/debugger/reference/idebugmethodfield.md) respectivement. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) est une autre interface dérivée importante qui représente des symboles contenant d’autres symboles, comme des méthodes ou des classes. L’interface `IDebugField` (et ses dérivés) est généralement implémentée par le fournisseur de symboles.

     Un `IDebugField` objet peut être utilisé pour trouver le nom et le type d’un symbole et, avec un objet [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) peut être utilisé pour trouver sa valeur.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Représente les bits réels de la valeur de l’exécution d’un symbole. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) prend un objet [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) qui représente un symbole, et renvoie un objet [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) La méthode [GetValue renvoie](../../extensibility/debugger/reference/idebugobject-getvalue.md) la valeur du symbole dans un tampon de mémoire. Un DE implémente généralement cette interface pour représenter la valeur d’une propriété dans la mémoire.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Cette interface représente l’évaluateur d’expression lui-même. La méthode clé est [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), qui renvoie une interface [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Cette interface représente une expression analysée prête à être évaluée. La méthode clé est [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) qui renvoie un IDebugProperty2 représentant la valeur et le type de l’expression.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Cette interface représente une valeur et son type et est le résultat d’une évaluation d’expression.

## <a name="see-also"></a>Voir aussi
- [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)
