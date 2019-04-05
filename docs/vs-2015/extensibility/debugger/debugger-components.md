---
title: Composants du débogueur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953377"
---
# <a name="debugger-components"></a>Composants du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur est implémenté comme un VSPackage et gère la session de débogage entière. La session de débogage comprend les éléments suivants :  
  
- **Déboguer le Package :** Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur fournit la même interface utilisateur, quel que soit ce qui est en cours de débogage.  
  
- **Gestionnaire de débogage de session (SDM) :** Fournit une interface de programmation cohérente pour la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur pour la gestion d’un grand nombre de moteurs de débogage. Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
- **Gestionnaire de débogage de processus (PDM) :** Gère toutes les instances en cours d’exécution de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], une liste de tous les programmes qui peuvent être ou sont en cours de débogage. Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
- **Déboguer le moteur de (dé) :** Est responsable de la surveillance d’un programme en cours de débogage, communiquer l’état du programme en cours d’exécution pour le SDM et le responsables prestations Professional direct et l’interaction avec l’évaluateur d’expression et le fournisseur de symboles pour fournir une analyse en temps réel de l’état de la mémoire d’un programme et variables. Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pour les langues prises en charge) et des fournisseurs tiers qui souhaitent prendre en charge de leur propres moment de l’exécution.  
  
- **Évaluateur d’expression (EE) :** Prend en charge pour l’évaluation dynamique de variables et expressions fournies par l’utilisateur lorsqu’un programme a été arrêté à un moment donné. Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pour les langues prises en charge) et des fournisseurs tiers qui souhaitent prendre en charge leur propre langue.  
  
- **Fournisseur de symboles (SP) :** Également appelé un gestionnaire de symboles, mappe les symboles de débogage d’un programme à une instance en cours d’exécution du programme afin que les informations explicites peuvent être fournies (par exemple, le débogage au niveau de code source et l’évaluation de l’expression). Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pour le Common Language Runtime (CLR) symboles et la base de données du programme [PDB] symbol format de fichier) et par des fournisseurs tiers qui ont leur propre méthode propriétaire de stocker les informations de débogage.  
  
  Le diagramme suivant illustre les relations entre ces éléments du débogueur Visual Studio.  
  
  ![Vue d’ensemble des composants de débogage](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>Dans cette section  
 [Déboguer le package](../../extensibility/debugger/debug-package.md)  
 Décrit le package de débogage, qui s’exécute dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell et traite l’intégralité de l’interface utilisateur.  
  
 [Gestionnaire du débogage de processus](../../extensibility/debugger/process-debug-manager.md)  
 Fournit une vue d’ensemble des fonctionnalités de PDM, ce qui est le Gestionnaire de processus qui peuvent être débogués.  
  
 [Gestionnaire du débogage de session](../../extensibility/debugger/session-debug-manager.md)  
 Définit le SDM, qui fournit une vue unifiée de la session de débogage à l’IDE. Le SDM gère l’Allemagne.  
  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)  
 Décrit les services de débogage qui fournit de l’Allemagne.  
  
 [Modes de fonctionnement](../../extensibility/debugger/operational-modes.md)  
 Fournit une vue d’ensemble des trois modes dans lesquels l’IDE peut fonctionner : mode Création, en mode exécution et le mode arrêt. Mécanismes de transition sont également abordés.  
  
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)  
 Explique l’objectif de la EE en cours d’exécution.  
  
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)  
 Explique comment, à l’implémentation, le fournisseur de symboles évalue variables et expressions.  
  
 [Visualiseur de type et visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Explique ce qu’un visualiseur de type et la visionneuse personnalisée sont et quel rôle joué par l’évaluateur d’expression prise en charge à la fois.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architectures débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le D’opère simultanément dans le code, documentation et contextes d’évaluation d’expression. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation pertinente à ce dernier.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
