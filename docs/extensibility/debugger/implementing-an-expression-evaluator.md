---
title: "L’impl&#233;mentation d’un &#233;valuateur d’Expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluateurs d'expression"
  - "débogage des évaluateurs d’expression [Debugging SDK],"
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# L’impl&#233;mentation d’un &#233;valuateur d’Expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Évaluation d’une expression est une interaction complexe entre le moteur de débogage \(DE\), le fournisseur de symboles \(SP\), l’objet binder et l’évaluateur d’expression \(EE\) lui\-même. Ces quatre composants sont connectés par les interfaces qui sont implémentées par un composant et consommés par un autre.  
  
 Le EE prend une expression de la DE sous la forme d’une chaîne et analyse ni évalue. Le EE implémente les interfaces suivantes, qui sont consommés par le DE :  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 Le EE appelle l’objet binder, fourni par le DE, pour obtenir la valeur des symboles et des objets. Le EE consomme les interfaces suivantes, qui sont implémentées par le DE :  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implémente le EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md).`IDebugProperty2` fournit le mécanisme permettant de décrire le résultat de l’évaluation d’une expression, comme une variable locale, un type primitif ou un objet, à Visual Studio, qui affiche ensuite les informations appropriées dans le **variables locales**, **Espion**, ou **immédiat** fenêtre.  
  
 Le SP est donné à la EE par le DE lorsqu’il demande des informations. La procédure stockée implémente des interfaces qui décrivent les adresses et les champs, tels que les interfaces suivantes et leurs dérivés :  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 Le EE consomme toutes ces interfaces.  
  
## Dans cette section  
 [Stratégie d’implémentation évaluateur expression](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Définit un processus en trois étapes pour la stratégie d’implémentation expression évaluateur \(EE\).  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)