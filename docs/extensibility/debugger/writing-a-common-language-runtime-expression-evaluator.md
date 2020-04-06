---
title: Rédaction d’un évaluateur de l’expression de course linguistique commune (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712322"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Rédaction d’un évaluateur commun d’expression de course de langue
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’évaluateur d’expression (EE) fait partie d’un moteur de débogé (DE) qui gère la syntaxe et la sémantique du langage de programmation qui a produit le code étant débogé. Les expressions doivent être évaluées dans le contexte d’un langage de programmation. Par exemple, dans certaines langues, l’expression « A-B » signifie « la somme de A et B ». Dans d’autres langues, la même expression peut signifier « A ou B ». Ainsi, une EE séparée doit être écrite pour chaque langage de programmation qui génère du code d’objet à déboiser dans le Visual Studio IDE.

 Certains aspects de l’ensemble de déboiffage Visual Studio doivent interpréter le code dans le contexte du langage de programmation. Par exemple, lorsque l’exécution s’arrête à un point d’arrêt, toute expression que l’utilisateur a tapée dans une fenêtre **de montre** doit être évaluée et affichée. L’utilisateur peut modifier la valeur d’une variable locale en tapant une expression dans une fenêtre **de montre** ou dans la fenêtre **immédiate.**

## <a name="in-this-section"></a>Contenu de cette section
 [Évaluation de l’heure d’exécution et de l’expression des langues courantes](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Explique que lorsque vous intègrez un langage de programmation propriétaire dans le Visual Studio IDE, l’écriture d’une EE capable d’évaluer les expressions dans le contexte de la langue propriétaire vous permet de compiler à un langage intermédiaire Microsoft (MSIL) sans écrire un moteur de déboissaille.

 [Architecture d’évaluateur d’expression](../../extensibility/debugger/expression-evaluator-architecture.md) Discute de la façon de mettre en œuvre les interfaces EE requises et d’appeler le fournisseur de symboles de temps d’exécution de langue commune (SP) et les interfaces de liant.

 [Enregistrer un évaluateur d’expression](../../extensibility/debugger/registering-an-expression-evaluator.md) Note que l’EE doit s’inscrire comme une usine de classe avec à la fois le temps courant de la langue et visual Studio environnements runtime.

 [Mettre en œuvre un évaluateur d’expression](../../extensibility/debugger/implementing-an-expression-evaluator.md) Décrit comment le processus d’évaluation d’une expression comprend le moteur de débogé (DE), le fournisseur de symbole (SP), l’objet de liant, et l’évaluateur d’expression (EE).

 [Afficher les habitants](../../extensibility/debugger/displaying-locals.md) Décrit comment, lorsque l’exécution s’arrête, le paquet de débog appelle le DE pour obtenir une liste de variables et d’arguments locaux.

 [Évaluer l’expression d’une fenêtre de montre](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Documente comment le paquet de débopathie Visual Studio appelle le DE pour déterminer la valeur actuelle de chaque expression dans sa liste de surveillance.

 [Modifier la valeur d’un](../../extensibility/debugger/changing-the-value-of-a-local.md) Explique qu’en changeant la valeur d’un local, chaque ligne de la fenêtre Locals a un objet associé qui fournit le nom, le type et la valeur actuelle d’un local.

 [Implémenter des visualisateurs de type et des téléspectateurs personnalisés](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Explique quelle interface doit être implémentée par quel composant pour prendre en charge les visualisateurs de type et les téléspectateurs personnalisés.

## <a name="see-also"></a>Voir aussi
 [Visual Studio débbugger extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
