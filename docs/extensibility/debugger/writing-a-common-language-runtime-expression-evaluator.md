---
title: Écriture d’un évaluateur d’expression Common Language Runtime | Microsoft Docs
description: En savoir plus sur l’écriture d’un évaluateur d’expression pour le common language runtime, qui évalue les expressions dans le langage de code en cours de débogage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 658158785d8f8a9376f5357ae2b869f6ad2e2271
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091394"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Écriture d’un évaluateur d’expression common language runtime
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluateur d’expression (EE) est la partie d’un moteur de débogage (DE) qui gère la syntaxe et la sémantique du langage de programmation qui a produit le code en cours de débogage. Les expressions doivent être évaluées dans le contexte d’un langage de programmation. Par exemple, dans certains langages, l’expression « A + B » signifie « la somme de A et B ». Dans d’autres langues, la même expression peut signifier « A ou B ». Par conséquent, un EE distinct doit être écrit pour chaque langage de programmation qui génère le code objet à déboguer dans l’IDE de Visual Studio.

 Certains aspects du package de débogage Visual Studio doivent interpréter le code dans le contexte du langage de programmation. Par exemple, lorsque l’exécution s’arrête à un point d’arrêt, toutes les expressions que l’utilisateur a tapées dans une fenêtre **Espion** doivent être évaluées et affichées. L’utilisateur peut modifier la valeur d’une variable locale en tapant une expression dans une fenêtre **Espion** ou dans la fenêtre **exécution** .

## <a name="in-this-section"></a>Dans cette section
 [Common Language Runtime et évaluation des expressions](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Explique que lorsque vous intégrez le langage de programmation propriétaire dans l’IDE de Visual Studio, l’écriture d’un EE capable d’évaluer des expressions dans le contexte du langage propriétaire vous permet de compiler en langage MSIL (Microsoft Intermediate Language) sans écrire de moteur de débogage.

 [Architecture](../../extensibility/debugger/expression-evaluator-architecture.md) de l’évaluateur d’expression Explique comment implémenter les interfaces EE requises et appeler le fournisseur de symboles (SP) common language runtime et les interfaces de Binder.

 [Inscrire un évaluateur d’expression](../../extensibility/debugger/registering-an-expression-evaluator.md) Remarque que l’EE doit s’inscrire en tant que fabrique de classe avec les common language runtime et les environnements d’exécution Visual Studio.

 [Implémenter un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md) Décrit comment le processus d’évaluation d’une expression comprend le moteur de débogage (DE), le fournisseur de symboles (SP), l’objet Binder et l’évaluateur d’expression (EE).

 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md) Décrit comment, lorsque l’exécution s’interrompt, le package de débogage appelle le pour obtenir une liste de variables locales et d’arguments.

 [Évaluer une expression de fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Décrit comment le package DE débogage Visual Studio appelle la méthode de pour déterminer la valeur actuelle de chaque expression dans sa liste de suivi.

 [Modifier la valeur d’un local](../../extensibility/debugger/changing-the-value-of-a-local.md) Explique que, lors de la modification de la valeur d’une variable locale, chaque ligne de la fenêtre variables locales a un objet associé qui fournit le nom, le type et la valeur actuelle d’un local.

 [Implémenter des visualiseurs de type et des visionneuses personnalisées](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Explique quelle interface doit être implémentée par le composant pour prendre en charge les visualiseurs de type et les visionneuses personnalisées.

## <a name="see-also"></a>Voir aussi
 [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
