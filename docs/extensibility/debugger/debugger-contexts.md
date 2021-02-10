---
title: Contextes du débogueur | Microsoft Docs
description: 'Découvrez comment le moteur de débogage de Visual Studio fonctionne dans des contextes distincts : contexte de code, contexte de documentation ou position et contexte d’évaluation d’expression.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89d2da35fb7ffa81ec9f6a882e6b35d42fc8f00c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952432"
---
# <a name="debugger-contexts"></a>Contextes du débogueur
Lors du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, le moteur de débogage (de) fonctionne simultanément dans plusieurs contextes distincts, comme suit :

- Le contexte de code, qui décrit l’emplacement actuel dans le flux d’exécution d’un programme.

- Le contexte de documentation ou la position, qui décrit la position actuelle dans un document source.

- Le contexte d’évaluation de l’expression, qui décrit le contexte dans lequel l’évaluation de l’expression aura lieu.

## <a name="in-this-section"></a>Dans cette section
 [Contexte de code](../../extensibility/debugger/code-context.md) Décrit le contexte de code comme une adresse dans le flux d’instructions d’un programme dans les architectures d’exécution actuelles et dans les langages non traditionnels, où le code ne peut pas être représenté par des instructions, mais d’autres moyens.

 [Position du document](../../extensibility/debugger/document-position.md) Définit la position du document dans le débogage Visual Studio à l’aide d’une abstraction d’une position dans un fichier source comme connu de l’IDE.

 [Contexte de document](../../extensibility/debugger/document-context.md) Décrit ce que représente le contexte de document dans le débogage Visual Studio par rapport à un fichier source. Explique également comment le gestionnaire de symboles mappe un contexte de code au contexte de documentation.

 [Contexte d’évaluation](../../extensibility/debugger/expression-evaluation-context.md) de l’expression Fournit des informations sur un contexte d’évaluation d’expression dans Visual Studio. Par exemple, un contexte d’évaluation d’expression associé à un frame de pile fournit le contexte pour l’évaluation des variables locales, des paramètres de méthode et des membres de classe.

## <a name="related-sections"></a>Sections connexes
 [Concepts de débogage](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux du débogage.

 [Déboguer des composants](../../extensibility/debugger/debugger-components.md) Fournit une vue d’ensemble des composants de débogage de Visual Studio, notamment le moteur DE débogage (DE), l’évaluateur d’expression (EE) et le gestionnaire de symboles (SH).

 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers différentes tâches de débogage, telles que le lancement d’un programme et l’évaluation d’expressions.
