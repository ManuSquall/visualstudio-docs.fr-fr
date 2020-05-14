---
title: Composants Debugger (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739008"
---
# <a name="debugger-components"></a>Composants Debugger
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débbugger est implémenté comme un VSPackage et gère l’ensemble de la session de débog. La session de débogé comprend les éléments suivants :

- **Forfait Debug:** Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débbugger fournit la même interface utilisateur, peu importe ce qui est débogé.

- **Responsable de débogé de session (SDM) :** Fournit une interface programmatique [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cohérente au Debugger pour la gestion d’une variété de moteurs de déboges. Il est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]mis en œuvre par .

- **Gestionnaire de débogé de processus (PDM) :** Gère, pour tous [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]les instances en cours d’exécution de , une liste de tous les programmes qui peuvent être ou sont débogés. Il est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]mis en œuvre par .

- **Moteur Debug (DE):** Est responsable de la surveillance d’un programme en cours de déboguer, de communiquer l’état du programme en cours d’exécution au SDM et au PDM, et d’interagir avec l’évaluateur d’expression et le fournisseur de symboles afin de fournir une analyse en temps réel de l’état de la mémoire et des variables d’un programme. Il est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mis en œuvre par (pour les langues qu’il prend en charge) et par des fournisseurs tiers qui veulent prendre en charge leur propre temps d’exécution.

- **Évaluateur d’expression (EE) :** Fournit un soutien pour évaluer dynamiquement les variables et expressions fournies par l’utilisateur lorsqu’un programme a été arrêté à un moment donné. Il est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mis en œuvre par (pour les langues qu’il prend en charge) et par des fournisseurs tiers qui veulent prendre en charge leur propre langue.

- **Fournisseur de symboles (SP) :** Aussi appelé gestionnaire de symbole, cartographie les symboles de débogage d’un programme à une instance en cours d’exécution du programme afin que des informations significatives peuvent être fournies (comme le débogage au niveau du code source et l’évaluation de l’expression). Il est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mis en œuvre par (pour les symboles Common Language Runtime [CLR] et le format de fichier symbole Program DataBase [PDB]) et par des fournisseurs tiers qui ont leur propre méthode exclusive de stockage de l’information de débogage.

  Le diagramme suivant montre la relation entre ces éléments du débbugger Visual Studio.

  ![Vue d'ensemble du débogage de composants](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>Contenu de cette section
 [Paquet Debug](../../extensibility/debugger/debug-package.md) Discute de l’emballage de débog, qui s’exécute dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] coquille et gère toute l’interface utilisateur.

 [Gestionnaire de débogé de processus](../../extensibility/debugger/process-debug-manager.md) Fournit un aperçu des caractéristiques du PDM, qui est le gestionnaire des processus qui peuvent être déboisés.

 [Gestionnaire de débogé de session](../../extensibility/debugger/session-debug-manager.md) Définit le SDM, qui fournit une vue unifiée de la session de débog à l’IDE. Le SDM gère le DE.

 [Moteur Debug](../../extensibility/debugger/debug-engine.md) Documente les services de débogage que le DE fournit.

 [Modes opérationnels](../../extensibility/debugger/operational-modes.md) Fournit un aperçu des trois modes dans lesquels l’IDE peut fonctionner : mode de conception, mode d’exécution et mode de rupture. Les mécanismes de transition sont également discutés.

 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md) Explique le but de l’EE au moment de la course.

 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md) Discute comment, lors de la mise en œuvre, le fournisseur de symboles évalue les variables et les expressions.

 [Type visualisateur et visualiseur personnalisé](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Discute de ce qu’est un visualiseur de type et le visualiseur personnalisé et quel rôle l’évaluateur d’expression joue dans le soutien des deux.

## <a name="related-sections"></a>Sections connexes
 [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md) Décrit les principaux concepts architecturaux débogage.

 [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md) Explique comment le DE fonctionne simultanément dans les contextes d’évaluation du code, de la documentation et de l’expression. Décrit, pour chacun des trois contextes, l’emplacement, le poste ou l’évaluation qui lui est pertinent.

 [Tâches de débogé](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.

## <a name="see-also"></a>Voir aussi
- [Bien démarrer](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
