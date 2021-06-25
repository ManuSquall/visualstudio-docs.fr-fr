---
title: Interfaces d’évaluateur d’expression clés | Microsoft Docs
description: En savoir plus sur les interfaces que vous devez connaître lorsque vous écrivez un évaluateur d’expression, ainsi que le contexte d’évaluation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: abfa4018e763bbbac5ff788f401d0ceb76eb97a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901264"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces d’évaluateur d’expression clés
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Lors de l’écriture d’un évaluateur d’expression (EE), en même temps que le contexte d’évaluation, vous devez être familiarisé avec les interfaces suivantes.

## <a name="interface-descriptions"></a>Descriptions des interfaces

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Possède une méthode unique, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), qui obtient une structure de données qui représente le point d’exécution actuel. Cette structure de données est l’un des trois arguments que le moteur DE débogage passe à la méthode [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour évaluer une expression. Cette interface est généralement implémentée par le fournisseur de symboles.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     A la méthode de [liaison](../../extensibility/debugger/reference/idebugbinder-bind.md) , qui obtient la zone mémoire qui contient la valeur actuelle d’un symbole. Étant donné la méthode conteneur, représentée par un objet [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , et le symbole lui-même, représenté par un objet [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , `IDebugBinder::Bind` retourne la valeur du symbole. `IDebugBinder` est généralement implémenté par le DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Représente un type de données simple. Pour les types plus complexes, tels que les tableaux et les méthodes, utilisez respectivement les interfaces [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) et [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) dérivées. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) est une autre interface dérivée importante qui représente des symboles qui contiennent d’autres symboles, tels que des méthodes ou des classes. L' `IDebugField` interface (et ses dérivés) est généralement implémentée par le fournisseur de symboles.

     Un `IDebugField` objet peut être utilisé pour rechercher le nom et le type d’un symbole et, avec un objet [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) , peut être utilisé pour rechercher sa valeur.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Représente les bits réels de la valeur au moment de l’exécution d’un symbole. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) accepte un objet [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , qui représente un symbole, et retourne un objet [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) . La méthode [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) retourne la valeur du symbole dans une mémoire tampon. Un DE implémente généralement cette interface pour représenter la valeur d’une propriété en mémoire.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Cette interface représente l’évaluateur d’expression lui-même. La méthode Key est [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), qui retourne une interface [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Cette interface représente une expression analysée prête à être évaluée. La méthode clé est [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) qui retourne un IDebugProperty2 représentant la valeur et le type de l’expression.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Cette interface représente une valeur et son type et est le résultat d’une évaluation d’expression.

## <a name="see-also"></a>Voir aussi
- [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)
