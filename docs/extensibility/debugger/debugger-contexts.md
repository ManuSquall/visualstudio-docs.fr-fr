---
title: Contextes du débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fc77e24a1a9ca72d6f689247f0de6a9e0bf26cc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098933"
---
# <a name="debugger-contexts"></a>Contextes du débogueur
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, le moteur de débogage (dé) opère simultanément dans plusieurs contextes distinctes, comme suit :

- Le contexte de code, qui décrit l’emplacement actuel dans le flux de l’exécution d’un programme.

- Le contexte de la documentation ou de la position, qui décrit la position actuelle dans un document source.

- Le contexte d’évaluation expression, qui décrit le contexte dans les expressions évaluation aura lieu.

## <a name="in-this-section"></a>Dans cette section
 [Contexte de code](../../extensibility/debugger/code-context.md) contexte de code présente en tant qu’adresse dans le flux d’instructions d’un programme dans les architectures d’exécution d’aujourd'hui par rapport aux langages non traditionnel, où code ne peut pas être représenté par des instructions, mais d’autres moyens.

 [Emplacement de document](../../extensibility/debugger/document-position.md) définit la position du document dans le débogage de Visual Studio au moyen d’une abstraction d’une position dans un fichier source connues de l’IDE.

 [Contexte de document](../../extensibility/debugger/document-context.md) décrit quel contexte de document représente lors du débogage de Visual Studio par rapport à un fichier source. Explique également comment le Gestionnaire de symboles mappe un contexte de code au contexte de la documentation.

 [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md) fournit des informations sur un contexte d’évaluation d’expression dans Visual Studio. Par exemple, un contexte d’évaluation d’expression associé à un frame de pile fournit le contexte pour évaluer les variables locales, les paramètres de méthode et les membres de classe.

## <a name="related-sections"></a>Rubriques connexes
 [Déboguer des concepts](../../extensibility/debugger/debugger-concepts.md) décrit les principaux concepts architectures débogage.

 [Déboguer des composants](../../extensibility/debugger/debugger-components.md) fournit une vue d’ensemble de composants, qui incluent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (SH) de débogage de Visual Studio.

 [Déboguer des tâches](../../extensibility/debugger/debugging-tasks.md) contient des liens vers diverses tâches de débogage, telles que lancement d’un programme et l’évaluation des expressions.