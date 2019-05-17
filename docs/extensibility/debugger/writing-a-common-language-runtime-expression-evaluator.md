---
title: Écriture d’un évaluateur de Common Language Runtime | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c7ec2b6313ee27fc46c778f8b19e104b169273
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421466"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Écriture d’un évaluateur de common language runtime
> [!IMPORTANT]
> Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluateur d’expression (EE) est la partie d’un moteur de débogage (dé) qui gère la syntaxe et sémantique du langage de programmation qui a généré le code en cours de débogage. Expressions doivent être évaluées dans le contexte d’un langage de programmation. Par exemple, dans certaines langues, l’expression « A + B » signifie « la somme de A et b. » Dans d’autres langages, la même expression peut signifier « A ou b ». Par conséquent, un distinct EE doit être écrites pour chaque langage de programmation qui génère du code de l’objet à déboguer dans l’IDE Visual Studio.

 Certains aspects du package de débogage de Visual Studio doivent interpréter le code dans le contexte du langage de programmation. Par exemple, lorsque l’exécution s’arrête à un point d’arrêt, toutes les expressions l’utilisateur a tapé dans un **espion** fenêtre doit être évaluée et affichée. L’utilisateur peut modifier la valeur d’une variable locale en tapant une expression dans une **espion** fenêtre ou dans le **immédiat** fenêtre.

## <a name="in-this-section"></a>Dans cette section
 [Common language runtime et expression l’évaluation](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) explique que lors de l’intégration de langage de programmation propriétaire dans l’IDE de Visual Studio, écrire un EE capable de l’évaluation des expressions dans le contexte de la langue de propriétaire vous permet de compiler en un langage intermédiaire de Microsoft (MSIL) sans avoir à écrire un moteur de débogage.

 [Architecture d’évaluateur d’expression](../../extensibility/debugger/expression-evaluator-architecture.md) explique comment implémenter les interfaces requises EE et appeler le fournisseur de symboles runtime du common language (SP) et les interfaces de classeurs.

 [Inscrire un évaluateur d’expression](../../extensibility/debugger/registering-an-expression-evaluator.md) Notes que le EE doit s’inscrire en tant qu’une fabrique de classe avec le common language runtime et les environnements d’exécution de Visual Studio.

 [Implémenter un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md) décrit comment le processus d’évaluation d’expression inclut le moteur de débogage (DE), le fournisseur de symboles (SP), l’objet de classeur et l’évaluateur d’expression (EE).

 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md) décrit comment, lors de l’exécution s’arrête, le package de débogage appelle le DE pour obtenir la liste des variables locales et des arguments.

 [Évaluer une expression de la fenêtre Espion](../../extensibility/debugger/evaluating-a-watch-window-expression.md) comment le package de débogage de Visual Studio appelle le DE pour déterminer la valeur actuelle de chaque expression dans sa liste de suivi des Documents.

 [Modifiez la valeur d’une variable locale](../../extensibility/debugger/changing-the-value-of-a-local.md) explique que modifier la valeur d’une variable locale, chaque ligne de la fenêtre variables locales est associé un objet qui fournit le nom, le type et la valeur actuelle d’une variable locale.

 [Implémenter des visualiseurs de type et les visionneuses personnalisées](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) explique quelle interface doit être implémentée par le composant à prendre en charge les visualiseurs de type et les visionneuses personnalisées.

## <a name="see-also"></a>Voir aussi
 [Extensibilité du débogueur Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)