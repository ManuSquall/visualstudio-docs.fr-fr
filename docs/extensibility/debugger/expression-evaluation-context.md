---
title: "Contexte d’évaluation d’expression | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ac80a3fcf3a7f75be3f23dd1350da047ccbb393
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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