---
title: Implémentation d’un évaluateur d’Expression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a4e4fdfa9d1c5ee8a5ad4284ae687b44ad7f4d5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956985"
---
# <a name="implement-an-expression-evaluator"></a>Implémenter un évaluateur d’expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Évaluation d’une expression est une interaction complexe entre le moteur de débogage (DE), le fournisseur de symboles (SP), l’objet de classeur et l’évaluateur d’expression (EE). Ces quatre composants sont connectés par les interfaces qui sont implémentées par un composant et consommées par un autre.  
  
 Le EE prend une expression à partir de l’Allemagne sous la forme d’une chaîne et analyse ni n’évalue. Le EE exécute les interfaces suivantes, qui sont consommés par le DE :  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  Le EE appelle l’objet de classeur, fourni par l’Allemagne, pour obtenir la valeur des symboles et des objets. Le EE consomme les interfaces suivantes, qui sont implémentées par le DE :  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Exécute le EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fournit le mécanisme permettant de décrire le résultat d’une évaluation d’expression, tel qu’une variable locale, une primitive ou un objet à Visual Studio, il affiche ensuite les informations appropriées dans le **variables locales**, **espion** , ou **immédiat** fenêtre.  
  
  La procédure stockée est fournie pour le EE par le DE lorsqu’il demande d’informations. La procédure stockée s’exécute les interfaces qui décrivent les adresses et les champs, tels que les interfaces suivantes et leurs dérivés :  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  Le EE consomme toutes ces interfaces.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Stratégie d’implémentation évaluateur expression](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Définit un processus en trois étapes pour la stratégie d’implémentation expression évaluateur (EE).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)