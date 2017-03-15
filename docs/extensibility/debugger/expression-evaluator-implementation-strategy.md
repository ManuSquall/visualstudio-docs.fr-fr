---
title: "Strat&#233;gie d’impl&#233;mentation &#233;valuateur expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation d’expression, stratégie d’implémentation"
  - "moteurs de débogage, stratégies d’implémentation"
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Strat&#233;gie d’impl&#233;mentation &#233;valuateur expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Pour créer rapidement un évaluateur d’expression \(EE\) consiste à implémenter tout d’abord le code minimal nécessaire pour afficher les variables locales dans le **variables locales** fenêtre. Il est utile de comprendre que chaque ligne dans le **variables locales** affiche le nom, le type et la valeur d’une variable locale, et que les trois sont représentées par une [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet. Le nom, le type et la valeur d’une variable locale peuvent être obtenus à partir d’un `IDebugProperty2` en appelant son [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) \(méthode\). Pour plus d’informations sur l’affichage des variables locales dans le **variables locales** fenêtre, consultez la page [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## Discussion  
 Une séquence de mise en oeuvre éventuelle commence par l’implémentation de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Le [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) et le [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) méthodes doivent être implémentées pour afficher les variables locales. L’appel `IDebugExpressionEvaluator::GetMethodProperty` retourne un `IDebugProperty2` objet qui représente une méthode : autrement dit, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objet. Les méthodes elles\-mêmes ne sont pas affichés dans le **variables locales** fenêtre.  
  
 Le [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) méthode doit être implémentée ensuite. Le moteur de débogage \(DE\) appelle cette méthode pour obtenir la liste des variables locales et des arguments en transmettant `IDebugProperty2::EnumChildren` un `guidFilter` argument `guidFilterLocalsPlusArgs`.`IDebugProperty2::EnumChildren` appels [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) et [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinaison des résultats dans une énumération unique. Pour plus d'informations, consultez [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## Voir aussi  
 [L’implémentation d’un évaluateur d’Expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md)