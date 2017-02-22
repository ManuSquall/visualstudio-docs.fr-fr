---
title: "&#201;valuateur d&#39;expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "expressions (débogage SDK)"
  - "évaluation de l'expression [Debugging SDK], le débogage"
  - "évaluation d’expression"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# &#201;valuateur d&#39;expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les évaluateurs \(EE\) d'expression vérifiez la syntaxe d'un langage pour analyser et évaluer des variables et des expressions au moment de l'exécution, leur permettant d'afficher par l'utilisateur lorsque l'IDE est en mode arrêt.  
  
## Utilisation des évaluateurs d'expression  
 Les expressions sont créées à l'aide de la méthode d' [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , comme suit :  
  
1.  le moteur de débogage \(DE\) implémente l'interface d' [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2.  Le package de débogage obtient un objet d' `IDebugExpressionContext2` d'une interface d' [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) puis appelle la méthode d' `IDebugStackFrame2::ParseText` dessus pour obtenir un objet d' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3.  le package de débogage appelle la méthode d' [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou la méthode d' [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir la valeur de l'expression.  `IDebugExpression2::EvaluateAsync` est appelé de la commande\/fenêtre exécution.  tout autre appel `IDebugExpression2::EvaluateSync`de composants d'interface utilisateur.  
  
4.  Le résultat de l'évaluation de l'expression est un objet d' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , qui contient le nom, le type, et la valeur du résultat de l'évaluation d'une expression.  
  
 Pendant l'évaluation de l'expression, l'évaluateur d'expression a besoin de données du composant fournisseur de symbole.  Le fournisseur de symbole fournit des informations symboliques utilisées pour identifier et comprendre l'expression analysée.  
  
 Lorsque l'évaluation de l'expression asynchrone est terminée, un événement asynchrone est envoyé par le De via le gestionnaire de débogage de session \(SDM\) pour informer l'IDE que l'évaluation de l'expression est terminée.  Lorsque l'évaluation de l'expression synchrone est terminée, le résultat de l'évaluation est retournée par l'appel à la méthode d' `IDebugExpression2::EvaluateSync` .  
  
## remarques d'implémentation  
 Les moteurs de débogage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comptent parler avec l'évaluateur d'expression à l'aide de les interfaces \(CLR\) du common langage runtime.  Par conséquent, un évaluateur d'expression qui fonctionne avec les moteurs de débogage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] doit prendre en charge le CLR \(une liste complète de toutes les interfaces de débogage du CLR peut être récupérée dans debugref.doc, qui fait partie de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]\).  
  
## Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)