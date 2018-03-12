---
title: "Composants du débogueur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1137c8c5c6041b41e8cbdc0e13d43b6188bd1b1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-components"></a>Composants du débogueur
Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur est implémenté comme un VSPackage et gère la session de débogage entière. La session de débogage comprend les éléments suivants :  
  
-   **Package de débogage :** le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur fournit la même interface utilisateur, quel que soit ce qui est en cours de débogage.  
  
-   **Gestionnaire de session de débogage (SDM) :** fournit une interface de programmation cohérente pour la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogueur pour la gestion d’un ensemble de moteurs de débogage. Elle est implémentée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Gestionnaire de processus de débogage (PDM) :** gère, toutes les instances en cours d’exécution de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], une liste de tous les programmes qui peuvent être ou sont en cours de débogage. Elle est implémentée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Déboguer le moteur (DE) :** est responsable de la surveillance d’un programme en cours de débogage, la communication de l’état du programme en cours d’exécution pour le SDM et PDM et interagir avec l’évaluateur d’expression et le fournisseur de symbole pour fournir une analyse en temps réel de la état de la mémoire et les variables d’un programme. Elle est implémentée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pour les langues prises en charge) et les fournisseurs tiers qui souhaitent prendre en charge leur propres moment de l’exécution.  
  
-   **Évaluateur d’expression (EE) :** fournit la prise en charge pour l’évaluation dynamique de variables et les expressions fournies par l’utilisateur lorsqu’un programme a été arrêté à un moment donné. Elle est implémentée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pour les langues prises en charge) et les fournisseurs tiers qui souhaitent prendre en charge leur propre langue.  
  
-   **Fournisseur de symboles (SP) :** appelé également un gestionnaire de symboles, mappe les symboles de débogage d’un programme à une instance en cours d’exécution du programme afin que des informations explicites peuvent être fournies (par exemple, le niveau de code source de débogage et l’expression d’évaluation). Elle est implémentée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (pour le Common Language Runtime (CLR) la base de données du programme [fichier PDB] et les symboles de symboles de format de fichier) et par des fournisseurs tiers qui ont leur propre méthode propriétaire du stockage des informations de débogage.  
  
 Le diagramme suivant montre la relation entre ces éléments du débogueur Visual Studio.  
  
 ![Vue d’ensemble des composants de débogage](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>Dans cette section  
 [Déboguer le package](../../extensibility/debugger/debug-package.md)  
 Décrit le package de débogage, qui s’exécute dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] du shell et gère l’ensemble de l’interface utilisateur.  
  
 [Gestionnaire du débogage de processus](../../extensibility/debugger/process-debug-manager.md)  
 Fournit une vue d’ensemble des fonctionnalités de PDM, ce qui est le Gestionnaire de processus qui peuvent être débogués.  
  
 [Gestionnaire du débogage de session](../../extensibility/debugger/session-debug-manager.md)  
 Définit le SDM, qui fournit une vue unifiée de la session de débogage à l’IDE. Le SDM gère le DE.  
  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)  
 Documente la DE fournit les services de débogage.  
  
 [Modes de fonctionnement](../../extensibility/debugger/operational-modes.md)  
 Fournit une vue d’ensemble des trois modes dans lequel l’environnement IDE peut fonctionner : mode Création, en mode exécution et le mode arrêt. Mécanismes de transition sont également décrites.  
  
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)  
 Explique l’objectif de la EE au moment de l’exécution.  
  
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)  
 Explique comment, à l’implémentation, le fournisseur de symbole évalue variables et les expressions.  
  
 [Visualiseur de type et visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Explique ce qu’un visualiseur de type et la visionneuse personnalisée se trouvent et quel rôle joué par l’évaluateur d’expression dans la prise en charge.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts d’architecture débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le DE fonctionne simultanément dans le code, la documentation et les contextes d’expression d’évaluation. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation appropriée à ce dernier.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)