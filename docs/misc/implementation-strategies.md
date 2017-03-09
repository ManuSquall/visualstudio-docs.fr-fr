---
title: "Strat&#233;gies d’impl&#233;mentation | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, stratégies d’implémentation"
ms.assetid: f5512d4e-666d-4934-bd42-9718fd7e4c06
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# Strat&#233;gies d’impl&#233;mentation
Vous pouvez étendre Visual Studio avec des compléments Automation, des VSPackages, des composants MEF \(Managed Extensibility Framework\), ou une combinaison des trois. En règle générale, les compléments sont plus faciles à développer mais ils sont moins puissants que les composants MEF ou les VSPackages. Les compléments peuvent appeler des interfaces d’extensibilité, et les VSPackages et les composants MEF peuvent accéder au modèle Automation Visual Studio. Vous pouvez combiner plusieurs approches différentes pour créer une solution efficace.  
  
 Vous pouvez écrire des VSPackages en code managé ou non managé. Nous vous recommandons d’écrire les nouveaux VSPackages en code managé à l’aide de l’infrastructure de package managé \(MPF, Managed Package Framework\). Presque tout ce qui peut être écrit en code non managé peut être implémenté plus facilement et en toute sécurité dans du code managé. Toutefois, les applications héritées écrites en code non managé continuent à s’exécuter dans Visual Studio.  
  
 Des extensions simples peuvent ajouter des fenêtres Outil ou envoyer des informations à des éléments d’interface utilisateur de Visual Studio, tels que la barre d’état ou la fenêtre de sortie. Des applications plus complexes peuvent être écrites en tant que hiérarchies Visual Studio, telles que l’Explorateur de serveurs. Vous pouvez obtenir encore plus de puissance en implémentant un projet, un éditeur ou un concepteur. Par exemple, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] sont eux\-mêmes implémentés en tant que services de langage.  
  
## Rubriques connexes  
 [Kit de développement logiciel \(SDK\) Visual Studio et Automation](../Topic/Visual%20Studio%20SDK%20and%20Automation.md)  
 Traite de l’utilisation de l’Automation, des VSPackages ou d’une combinaison pour créer des applications d’extensibilité Visual Studio.  
  
 [Kit de développement logiciel Visual Studio \(SDK\) et code managé](/visual-cpp/misc/visual-studio-sdk-and-managed-code)  
 Compare les différentes façons d’écrire un VSPackage dans du code managé.  
  
 [Concepts de l’IDE de Visual Studio](/visual-cpp/misc/visual-studio-ide-concepts)  
 Décrit les principes de base des VSPackages et comment utiliser un service.  
  
 [Extension des autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Traire des éléments d’application d’interface utilisateur communs dans Visual Studio, tels que les fenêtres État et Sortie.  
  
 [Hiérarchies dans Visual Studio](../extensibility/internals/hierarchies-in-visual-studio.md)  
 Fournit une vue d’ensemble des hiérarchies Visual Studio, qui sont affichées dans l’environnement de développement intégré \(IDE\) sous la forme d’arborescences de nœuds.  
  
 [Projets](../extensibility/internals/projects.md)  
 Fournit une vue d’ensemble des classes de solution et de projet.  
  
 [Éditeur et les Extensions de Service de langage](../extensibility/editor-and-language-service-extensions.md)  
 Montre comment étendre l’éditeur de code et de texte, et comment créer des concepteurs et éditeurs personnalisés.  
  
 [Extensibilité du Service de langage ancien](../extensibility/internals/legacy-language-service-extensibility.md)  
 Montre comment créer des services de langage.  
  
 [Référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Fournit une documentation de référence pour le VSSDK.  
  
## Voir aussi  
 [Commencer à développer des Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md)