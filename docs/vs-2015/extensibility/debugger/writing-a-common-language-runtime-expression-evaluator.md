---
title: Écriture d’un évaluateur de Common Language Runtime | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435278"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Écriture d’un évaluateur d’expression Common Language Runtime
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L’évaluateur d’expression (EE) est la partie d’un moteur de débogage (dé) qui gère la syntaxe et sémantique du langage de programmation qui a généré le code en cours de débogage. Expressions doivent être évaluées dans le contexte d’un langage de programmation. Par exemple, dans certaines langues, l’expression « A + B » signifie « la somme de A et b. » Dans d’autres langages, la même expression peut signifier « A ou b ». Par conséquent, un distinct EE doit être écrites pour chaque langage de programmation qui génère du code de l’objet à déboguer dans l’IDE Visual Studio.  
  
 Certains aspects du package de débogage de Visual Studio doivent interpréter le code dans le contexte du langage de programmation. Par exemple, lorsque l’exécution s’arrête à un point d’arrêt, toutes les expressions l’utilisateur a tapé dans un **espion** fenêtre doit être évaluée et affichée. En outre, l’utilisateur peut modifier la valeur d’une variable locale en tapant une expression dans une **espion** fenêtre ou dans le **immédiat** fenêtre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Common Language Runtime et évaluateur d’expression](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Explique que lorsque vous intégrez un langage de programmation propriétaire à l’IDE Visual Studio, écrire un EE capable de l’évaluation des expressions dans le contexte de la langue propriétaire vous permet de compiler un langage intermédiaire de Microsoft (MSIL) sans avoir à écrire un moteur de débogage.  
  
 [Architecture de l’évaluateur d'expression](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Explique comment implémenter les interfaces requises EE et appeler le fournisseur de symboles runtime du common language (SP) et les interfaces de classeurs.  
  
 [Inscription d’un évaluateur d’expression](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Indique que le EE doit s’inscrire en tant qu’une fabrique de classe avec le common language runtime et les environnements d’exécution de Visual Studio.  
  
 [Implémentation d’un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Décrit comment le processus d’évaluation d’expression inclut le moteur de débogage (DE), le fournisseur de symboles (SP), l’objet de classeur et l’évaluateur d’expression (EE).  
  
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)  
 Décrit comment, lors de l’exécution s’arrête, le package de débogage appelle le DE pour obtenir la liste des variables locales et des arguments.  
  
 [Évaluation d’une expression de fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Décrit comment le package de débogage de Visual Studio appelle le DE pour déterminer la valeur actuelle de chaque expression dans sa liste de suivi.  
  
 [Modification de la valeur d’une variable locale](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explique que modifier la valeur d’une variable locale, chaque ligne de la fenêtre variables locales est associé un objet qui fournit le nom, le type et la valeur actuelle d’une variable locale.  
  
 [Implémentation de visualiseurs de type et de visionneuses personnalisées](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Explique de quelle interface doit être implémentée par le composant à prendre en charge les visualiseurs de type et les visionneuses personnalisées.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du débogueur de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
