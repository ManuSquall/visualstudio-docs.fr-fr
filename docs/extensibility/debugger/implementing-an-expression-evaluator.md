---
title: Mise en œuvre d’un évaluateur de l’expression (fr) Microsoft Docs
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
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738541"
---
# <a name="implement-an-expression-evaluator"></a>Mettre en œuvre un évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluation d’une expression est une interaction complexe entre le moteur de débogé (DE), le fournisseur de symbole (SP), l’objet de liant, et l’évaluateur d’expression (EE). Ces quatre composants sont reliés par des interfaces qui sont implémentées par un composant et consommées par un autre.

 L’EE prend une expression de la DE sous la forme d’une chaîne et l’analyse ou l’évalue. L’EE exécute les interfaces suivantes, qui sont consommées par le DE :

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  L’EE appelle l’objet de reliure, fourni par le DE, pour obtenir la valeur des symboles et des objets. L’EE consomme les interfaces suivantes, qui sont implémentées par le DE :

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  L’EE fonctionne [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`fournit le mécanisme pour décrire le résultat d’une évaluation d’expression, telle qu’une variable locale, un primitif, ou un objet à Visual Studio, qui affiche ensuite les informations appropriées dans les **sections locales,** **Regarder**, ou fenêtre **immédiate.**

  Le SP est donné à l’EE par le DE quand il demande des informations. Le SP exécute des interfaces qui décrivent les adresses et les champs, tels que les interfaces suivantes et leurs dérivés :

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  L’EE consomme toutes ces interfaces.

## <a name="in-this-section"></a>Contenu de cette section
 [Stratégie de mise en œuvre de l’évaluateur d’expression](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Définit un processus en trois étapes pour la stratégie de mise en œuvre de l’évaluateur d’expression (EE).

## <a name="see-also"></a>Voir aussi
- [Rédaction d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
