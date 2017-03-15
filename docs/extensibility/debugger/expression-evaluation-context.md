---
title: "Contexte d&#39;&#233;valuation d&#39;expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation d'expression, contexte"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Contexte d&#39;&#233;valuation d&#39;expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, **un contexte d'évaluation de l'expression**:  
  
-   représente un contexte pour l'évaluation de l'expression.  En général, un contexte d'évaluation correspond à la portée lexicale dans laquelle pour évaluer les variables, les paramètres, les fonctions, les méthodes et.  Par exemple, un contexte d'évaluation de l'expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, des paramètres de méthode, et les membres de classe \(le cas échéant\).  
  
-   S'applique lorsqu'un programme a arrêté par un point d'arrêt.  L'expression est elle\-même une structure de données qui représente une expression analysée qui est prête pour la liaison et évaluer dans le contexte donné.  
  
     Plus en détail, les expressions sont créées à l'aide de la méthode d' [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .  Lorsqu'une expression est évaluée, elle génère une chaîne imprimable contenant le nom et le type de variable ou argument et sa valeur.  Cette chaîne est affichée dans la fenêtre Espion ou dans la fenêtre Variables locales de l'IDE.  
  
     donné `BSTR` et une interface d' [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un moteur de débogage \(DE\) peut créer une interface d' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) en analysant une expression.  À partir d'une interface d' `IDebugExpression2` , le De peut obtenir une valeur via l'évaluation d'une expression synchrone ou asynchrone.  Cette valeur, avec le nom et le type de la variable ou de l'argument, est envoyé à l'IDE pour l'affichage.  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)