---
title: "&#201;criture d&#39;un &#233;valuateur de Common Language Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluateurs d'expression, didacticiel"
  - "évaluation d'expression, exemples"
  - "didacticiel d'évaluateurs d'expression [Debugging SDK], le débogage"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# &#201;criture d&#39;un &#233;valuateur de Common Language Runtime
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d'implémenter des évaluateurs d'expression est déconseillée. Pour plus d'informations sur l'implémentation des évaluateurs d'expression CLR, consultez [évaluateurs d'Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d'évaluateur d'Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'évaluateur d'expression \(EE\) est la partie du moteur de débogage \(DE\) qui gère la syntaxe et la sémantique du langage de programmation qui a généré le code en cours de débogage. Expressions doivent être évaluées dans le contexte d'un langage de programmation. Par exemple, dans certaines langues, l'expression « A \+ B » signifie « la somme de A et b. » Dans d'autres langues, la même expression peut signifier « A ou B. » Par conséquent, un distinct EE doit être écrit pour chaque langage de programmation qui génère du code de l'objet à déboguer dans l'IDE de Visual Studio.  
  
 Certains aspects du package de débogage Visual Studio doivent interpréter le code dans le contexte du langage de programmation. Par exemple, lorsque l'exécution s'arrête au point d'arrêt, les expressions de l'utilisateur a tapé dans un **Espion** fenêtre doit être évaluée et affichée. En outre, l'utilisateur peut modifier la valeur d'une variable locale en tapant une expression dans une **Espion** fenêtre ou dans le **immédiat** fenêtre.  
  
## Dans cette section  
 [Common Language Runtime et l’évaluation d’Expression](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Explique que lorsque vous intégrez un langage de programmation propriétaire dans l'IDE de Visual Studio, écrire un EE capable de l'évaluation des expressions dans le contexte du langage propriétaire vous permet de compiler en un Microsoft intermediate language \(MSIL\) sans avoir à écrire un moteur de débogage.  
  
 [Architecture d’évaluateur d’expression](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Explique comment implémenter les interfaces EE et appeler le fournisseur de symbole runtime du common language \(SP\) et les interfaces de classeurs.  
  
 [L’inscription d’un évaluateur d’Expression](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Indique que le EE doit s'enregistrer comme une fabrique de classe avec le common language runtime et les environnements d'exécution de Visual Studio.  
  
 [L’implémentation d’un évaluateur d’Expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Décrit comment le processus d'évaluation d'expression inclut le moteur de débogage \(DE\), le fournisseur de symboles \(SP\), l'objet du classeur et l'évaluateur d'expression \(EE\).  
  
 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md)  
 Décrit comment, lors de l'exécution est suspendue, le package de débogage appelle la DE pour obtenir la liste des variables locales et les arguments.  
  
 [Évaluation d'une Expression de la fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Décrit comment le package de débogage Visual Studio appelle le DE pour déterminer la valeur actuelle de chaque expression dans sa liste de surveillance.  
  
 [Modification de la valeur des variables locales](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explique que modifier la valeur d'une variable locale, chaque ligne de la fenêtre variables locales est associé un objet qui fournit le nom, le type et la valeur actuelle d'une variable locale.  
  
 [L’implémentation de Type visualiseurs et les visionneuses personnalisées](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Décrit l'interface qui doit être implémentée par le composant pour prendre en charge les visualiseurs de type et les visionneuses personnalisées.  
  
## Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)