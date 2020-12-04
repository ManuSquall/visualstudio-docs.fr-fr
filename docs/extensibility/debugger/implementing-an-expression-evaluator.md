---
title: Implémentation d’un évaluateur d’expression | Microsoft Docs
description: En savoir plus sur l’évaluation d’une expression, qui implique le moteur de débogage, le fournisseur de symboles, l’objet Binder et l’évaluateur d’expression.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28989178ab726a9b274f66e0a9296f2bf49ead4a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559964"
---
# <a name="implement-an-expression-evaluator"></a>Implémenter un évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluation d’une expression est une interaction complexe entre le moteur DE débogage (DE), le fournisseur de symboles (SP), l’objet Binder et l’évaluateur d’expression (EE). Ces quatre composants sont connectés par des interfaces implémentées par un composant et consommées par un autre composant.

 L’EE prend une expression de l’une sous la forme d’une chaîne et l’analyse ou l’évalue. Le EE exécute les interfaces suivantes, qui sont consommées par l’un des éléments suivants :

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  L’EE appelle l’objet Binder fourni par le de, pour récupérer la valeur des symboles et des objets. L’EE utilise les interfaces suivantes, qui sont implémentées par l’un des éléments suivants :

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE exécute [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fournit le mécanisme pour décrire le résultat d’une évaluation d’expression, telle qu’une variable locale, une primitive ou un objet à Visual Studio, qui affiche ensuite les informations appropriées dans la fenêtre **variables locales**, **Espion** ou **exécution** .

  Le SP est donné au EE par le DE lorsqu’il demande des informations. Le SP exécute les interfaces qui décrivent les adresses et les champs, par exemple les interfaces suivantes et leurs dérivées :

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  L’EE utilise toutes ces interfaces.

## <a name="in-this-section"></a>Dans cette section
 [Stratégie d’implémentation](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) de l’évaluateur d’expression Définit un processus en trois étapes pour la stratégie d’implémentation de l’évaluateur d’expression (EE).

## <a name="see-also"></a>Voir aussi
- [Écriture d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
