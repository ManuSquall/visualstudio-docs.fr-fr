---
title: "Composants du d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (Visual Studio), composants"
  - "composants (Visual Studio SDK), le débogage"
  - "composants de débogage [Debugging SDK],"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Composants du d&#233;bogueur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le débogueur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est implémenté comme un VSPackage et gère la session de débogage entière.  la session de débogage comporte les éléments suivants :  
  
-   **package de débogage :** Le débogueur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit la même interface utilisateur n'importe quel est débogué.  
  
-   **gestionnaire de débogage de session \(SDM\) :** Fournit une interface de programmation cohérente au débogueur de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour la gestion de diverses moteurs de débogage.  il est implémenté par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **gestionnaire de processus de débogage \(PDM\) :** Gère, pour toutes les instances en cours de exécution de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], une liste de tous les programmes qui peuvent être ou sont débogués.  elle est implémentée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **moteur de débogage \(DE\) :** Permet de surveiller un programme en cours de débogage, en communiquant l'état du programme en cours de exécution au SDM et au PDM, et il interagit avec l'évaluateur d'expression et le fournisseur de symbole pour fournir l'analyse en temps réel de l'état de la mémoire et les variables d'un programme.  Il est implémenté par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(pour les langages prise en charge\) et les fournisseurs tiers qui souhaitent prendre en charge leur propre moment de l'exécution.  
  
-   **évaluateur d'expression \(EE\) :** Fournit la prise en charge d'évaluer dynamiquement des variables et des expressions fournies par l'utilisateur lorsqu'un programme a été arrêté par un point particulier.  Il est implémenté par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(pour les langages prise en charge\) et les fournisseurs tiers qui souhaitent prendre en charge leurs propres langages.  
  
-   **fournisseur de symbole \(SP\) :** A également appelé un gestionnaire de symboles, mappe les symboles de débogage d'un programme à une instance en cours de exécution du programme afin que les informations explicites puissent être fournies \(comme le débogage et l'évaluation de l'expression de source\-code\-niveau\).  Il est implémenté par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(pour les symboles du common langage runtime CLR \[\] et le format des fichiers de symboles de base de données du programme \(PDB \[\]\) et par les fournisseurs tiers qui ont leur propre méthode propriétaire pour enregistrer les informations de débogage.  
  
 Le diagramme suivant illustre la relation entre ces éléments du débogueur Visual Studio.  
  
 ![Vue d'ensemble du débogage de composants](~/docs/extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## Dans cette section  
 [Déboguer le Package](../../extensibility/debugger/debug-package.md)  
 Décrit le package de débogage, qui s'exécute dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] écossent et les handles l'ensemble de l'interface utilisateur.  
  
 [Gestionnaire de processus de débogage](../../extensibility/debugger/process-debug-manager.md)  
 Fournit une vue d'ensemble des fonctionnalités du PDM, qui est le gestionnaire des processus qui peuvent être débogués.  
  
 [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)  
 Définit le SDM, qui fournit un affichage unifié de la session de débogage à l'IDE.  Le SDM gère le De.  
  
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)  
 documente les services de débogage que le De fournit.  
  
 [Modes de fonctionnement](../../extensibility/debugger/operational-modes.md)  
 Fournit une vue d'ensemble des trois modes dans lesquels l'IDE peut s'exécuter : mode Design, mode exécution, et mode arrêt.  Les mécanismes de transition sont également traités.  
  
 [Évaluateur d'expression](../../extensibility/debugger/expression-evaluator.md)  
 Explique l'objectif de l'évaluateur d'expression au moment de l'exécution.  
  
 [Fournisseur de symboles](../../extensibility/debugger/symbol-provider.md)  
 Explique comment, à l'implémentation, le fournisseur de symbole a des variables et des expressions.  
  
 [Visualiseur de type et de la visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Explique ce que sont un visualiseur de type et une visionneuse de personnalisé et le rôle de l'évaluateur d'expression lit en prenant en charge les deux.  
  
## Rubriques connexes  
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)  
 décrit les concepts architecturaux de débogage principal.  
  
 [Contextes de débogueur](../../extensibility/debugger/debugger-contexts.md)  
 Explique comment le De s'exécute simultanément dans le code, la documentation, et des contextes d'évaluation de l'expression.  Décrit, pour les trois contextes, de l'emplacement, de la position, ou l'évaluation pertinentes à celui\-ci.  
  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers différentes tâches de débogage, telles que exécuter un programme et évaluer des expressions.  
  
## Voir aussi  
 [Prise en main](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)