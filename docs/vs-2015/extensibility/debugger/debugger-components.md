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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200663"
---
# <a name="debugger-components"></a>Composants du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur est implémenté en tant que VSPackage et gère l’intégralité de la session de débogage. La session de débogage comprend les éléments suivants :  
  
- **Package de débogage :** Le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur fournit la même interface utilisateur, quel que soit le débogage.  
  
- **Gestionnaire de débogage de session (SDM) :** Fournit une interface de programmation cohérente au [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] débogueur pour la gestion d’un grand nombre de moteurs de débogage. Elle est implémentée par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Gestionnaire de débogage de processus (PDM) :** Gère, pour toutes les instances en cours d’exécution [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , une liste de tous les programmes qui peuvent être ou sont en cours de débogage. Elle est implémentée par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- **Moteur de débogage (de) :** Est responsable de la surveillance d’un programme en cours de débogage, de la communication de l’état du programme en cours d’exécution au SDM et à PDM, et de l’interaction avec l’évaluateur d’expression et le fournisseur de symboles pour fournir une analyse en temps réel de l’état de la mémoire et des variables d’un programme. Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pour les langages qu’il prend en charge) et des fournisseurs tiers qui souhaitent prendre en charge leur propre temps d’exécution.  
  
- **Évaluateur d’expression (EE) :** Prend en charge l’évaluation dynamique des variables et des expressions fournies par l’utilisateur lorsqu’un programme a été arrêté à un point particulier. Il est implémenté par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pour les langages qu’il prend en charge) et des fournisseurs tiers qui souhaitent prendre en charge leurs propres langues.  
  
- **Fournisseur de symboles (SP) :** Également appelé gestionnaire de symboles, mappe les symboles de débogage d’un programme à une instance en cours d’exécution du programme afin que des informations explicites puissent être fournies (telles que le débogage au niveau du code source et l’évaluation de l’expression). Elle est implémentée par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (pour les symboles CLR (Common Language Runtime) et le format de fichier de symboles de la base de données du programme [PDB] et par les fournisseurs tiers qui possèdent leur propre méthode propriétaire de stockage des informations de débogage.  
  
  Le diagramme suivant montre la relation entre ces éléments du débogueur Visual Studio.  
  
  ![Vue d'ensemble du débogage de composants](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>Dans cette section  
 [Déboguer le package](../../extensibility/debugger/debug-package.md)  
 Décrit le package de débogage, qui s’exécute dans l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interpréteur de commandes et gère l’ensemble de l’interface utilisateur.  
  
 [Gestionnaire du débogage de processus](../../extensibility/debugger/process-debug-manager.md)  
 Fournit une vue d’ensemble des fonctionnalités de PDM, qui est le gestionnaire des processus qui peuvent être débogués.  
  
 [Gestionnaire du débogage de session](../../extensibility/debugger/session-debug-manager.md)  
 Définit le SDM, qui fournit une vue unifiée de la session de débogage à l’IDE. Le SDM gère le DE.  
  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)  
 Documente les services DE débogage fournis par le.  
  
 [Modes de fonctionnement](../../extensibility/debugger/operational-modes.md)  
 Fournit une vue d’ensemble des trois modes dans lesquels l’IDE peut fonctionner : mode Design, mode exécution et mode arrêt. Les mécanismes de transition sont également abordés.  
  
 [Évaluateur d’expression](../../extensibility/debugger/expression-evaluator.md)  
 Explique l’objectif du EE au moment de l’exécution.  
  
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)  
 Explique comment, lors de l’implémentation, le fournisseur de symboles évalue les variables et les expressions.  
  
 [Visualiseur de type et visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Décrit ce qu’est un visualiseur de type et une visionneuse personnalisée et le rôle joué par l’évaluateur d’expression dans pour prendre en charge les deux.  
  
## <a name="related-sections"></a>Sections connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 Décrit les principaux concepts architecturaux du débogage.  
  
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le fonctionne simultanément dans le code, la documentation et les contextes d’évaluation des expressions. Décrit, pour chacun des trois contextes, l’emplacement, la position ou l’évaluation qui s’y rapporte.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers différentes tâches de débogage, telles que le lancement d’un programme et l’évaluation d’expressions.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
