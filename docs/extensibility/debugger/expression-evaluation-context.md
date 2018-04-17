---
title: Contexte d’évaluation d’expression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1fade5bb18e59a1b9b9e2655ce01b0b5559484e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluation-context"></a>Contexte d’évaluation d’expression
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, une **contexte d’évaluation d’expression**:  
  
-   Représente un contexte pour l’évaluation d’expression. En règle générale, un contexte d’évaluation correspond à la portée lexicale dans laquelle évaluer les variables, les paramètres, les fonctions et les méthodes. Par exemple, un contexte d’évaluation d’expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, les paramètres de méthode et les membres de classe (le cas échéant).  
  
-   Il existe quand un programme s’est arrêté à un point d’arrêt. L’expression elle-même est une structure de données représentant une expression analysée est prête pour la liaison et l’évaluation dans le contexte donné.  
  
     Plus en détail, les expressions sont créées à l’aide de la [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode). Lorsqu’une expression est évaluée, elle génère une chaîne imprimable contenant le nom et le type de variable ou argument et sa valeur. Cette chaîne est affichée dans la fenêtre Espion ou dans la fenêtre variables locales de l’IDE.  
  
     Étant donné un `BSTR` et un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, un moteur de débogage (DE) peut créer un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface par l’analyse d’une expression. Étant donné un `IDebugExpression2` interface, le DE peut obtenir une valeur via l’évaluation d’expression synchrone ou asynchrone. Cette valeur, ainsi que le nom et le type de la variable ou un argument, est envoyée à l’IDE pour l’affichage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)