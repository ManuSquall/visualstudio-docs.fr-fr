---
title: Démarrer avec Debugger Extensibility (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738596"
---
# <a name="get-started-with-debugger-extensibility"></a>Commencer avec l’extéabilité de débbugger
Le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fournit l’information dont vous avez besoin pour créer et personnaliser les composants [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de débbugger utilisés pour déboquer les programmes de l’environnement.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le débogage a ajouté des améliorations découlant [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des tests d’utilisabilité étendu effectués sur les débogages précédents. Vous pouvez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliser le débogage pour passer par une application multi-langue, ou vous pouvez implémenter l’édition à la volée de variables tout en débogage d’applications et de solutions multi-langues.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le débogage est exécuté hors processus, le programme étant débogé et est donc moins intrusif dans l’espace de processus de la demande. Par conséquent, il est plus facile d’écrire des composants qui interagissent avec le débogage sans affecter votre programme de débogage.

 Pour mieux [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]utiliser le , vous devez être familier avec les éléments suivants:

- L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de développement intégré (IDE)

- Le langage de programmation de CMD

- ATL COM

## <a name="in-this-section"></a>Contenu de cette section
 [Feuille de route pour l’extension du débbugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Décrit le processus de mise en œuvre de débogage dans votre produit, en fonction de votre compilateur et de sa sortie.

 [Composants Debugger](../../extensibility/debugger/debugger-components.md) Fournit un aperçu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des composants de débogage, qui comprennent le moteur de débogage (DE), l’évaluateur d’expression (EE), et le gestionnaire de symbole (SH).

 [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux débogage.

 [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md) Explique comment le moteur de débogé (DE) fonctionne simultanément dans les contextes de code, de documentation et d’évaluation de l’expression. Décrit, pour chacun des trois contextes, l’emplacement, le poste ou l’évaluation qui lui est pertinent.

 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.
