---
title: Contextes Debugger (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738978"
---
# <a name="debugger-contexts"></a>Contextes Debugger
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage, le moteur de déboguer (DE) fonctionne simultanément dans plusieurs contextes distincts, comme suit :

- Le contexte du code, qui décrit l’emplacement actuel dans le flux d’exécution d’un programme.

- Le contexte ou la position de la documentation, qui décrit la position actuelle dans un document source.

- Le contexte d’évaluation de l’expression, qui décrit le contexte dans lequel l’évaluation de l’expression aura lieu.

## <a name="in-this-section"></a>Contenu de cette section
 [Contexte du code](../../extensibility/debugger/code-context.md) Discute du contexte du code comme adresse dans le flux d’instructions d’un programme dans les architectures d’aujourd’hui par rapport aux langues non traditionnelles, où le code peut ne pas être représenté par des instructions, mais d’autres moyens.

 [Position du document](../../extensibility/debugger/document-position.md) Définit la position du document dans Visual Studio débogage au moyen d’une abstraction d’une position dans un fichier source connu de l’IDE.

 [Contexte documentaire](../../extensibility/debugger/document-context.md) Discute du contexte documentaire que représente Visual Studio en ce qui concerne un fichier source. Discute également de la façon dont le gestionnaire de symbole cartographie un contexte de code au contexte de documentation.

 [Contexte d’évaluation de l’expression](../../extensibility/debugger/expression-evaluation-context.md) Fournit des informations sur un contexte d’évaluation d’expression dans Visual Studio. Par exemple, un contexte d’évaluation d’expression associé à un cadre de pile fournit le contexte pour évaluer les variables locales, les paramètres de la méthode et les membres du groupe.

## <a name="related-sections"></a>Sections connexes
 [Concepts de débbug](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux débogage.

 [Composants de débogé](../../extensibility/debugger/debugger-components.md) Fournit un aperçu des composants de débogage Visual Studio, qui comprennent le moteur de débogage (DE), l’évaluateur d’expression (EE) et le gestionnaire de symboles (SH).

 [Tâches de débogé](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.
