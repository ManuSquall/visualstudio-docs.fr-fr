---
title: "Architecture d’extensibilit&#233; Visual Studio | Microsoft Docs"
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
  - "Visual Studio, modèle d’environnement"
  - "modèle d’environnement, Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Architecture d’extensibilit&#233; Visual Studio
L'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est une infrastructure pour héberger les VSPackages et pour le rendre plus facile d'échanger les services partagés.  Un exemple de ce est la façon dont l'IDE implémente l'interface utilisateur \(UI\).  L'IDE fournit la fenêtre de conteneur et les barres d'outils et des menus par défaut.  Il fournit également une infrastructure riche COM qui rend l'interface utilisateur programmable.  Le modèle complète de gestion et de routage de commande permet aux utilisateurs une infrastructure ouverte qui fournit l'accès aux jeux de commandes existants et installés.  
  
## architecture d'extensibilité  
 l'illustration suivante montre l'architecture d'extensibilité de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  notez que le concept de l'application logiciel est absent.  Au lieu de cela, l'IDE héberge les logiciels, les VSPackages appelé, qui fournissent la fonctionnalité de l'application.  Cette fonctionnalité, à son tour, est partagée entre l'IDE comme services.  Services d'offrir de VSPackages qu'elles et d'autres utilisations de VSPackages.  La norme IDE offre également une large gamme de services, tels qu' <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui permettent d'accéder aux fonctionnalités de fenêtrage de l'IDE.  
  
 ![Graphique Architecture d’environnement](~/extensibility/internals/media/environment.gif "environment")  
vue généralisée de l'architecture de Visual Studio  
  
 Notez que la relation entre les VSPackages et services est bidirectionnelle.  Bien que les services d'utilisation de VSPackages aient offert par d'autres, ils peuvent également offrir des services de leurs propres à l'aide de l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  Cette architecture service\-basée s'est développée hors de l'implémentation du concepteur Microsoft ActiveX, dans lequel un service est un groupe d'interfaces connexes qui exécutent une tâche.  Du point de vue strict COM, toutes les interfaces d'un service particulier doivent être implémentées dans une classe COM unique.  
  
 L'IDE standard offre les services principaux, tels qu' <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, et <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>, qui sont utilisés par les VSPackages.  Le tableau suivant répertorie et décrit quelques\-uns de ces services.  Pour plus d'informations, consultez [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md).  
  
|Service de l'IDE|Description|  
|----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Permet d'accéder aux services de l'IDE de traitement la fonctionnalité de base, le VSPackages, et le Registre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit le fenêtrage de base et des fonctionnalités Interface utilisateur\-mise en relation dans l'IDE, telles que la capacité de créer des outils et des fenêtres de document.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit les fonctionnalités solution\-mise en relation de base, telle que la possibilité d'énumérer les projets, créer des projets, et le projet du moniteur change.|  
  
 En raison de leur intégration étroite via l'interaction des services partagés, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'IDE et les VSPackages sont étroitement interdépendants.  Toutefois, en dépit de leur interaction proche ils ont des responsabilités.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'IDE prend en charge les tâches suivantes :  
  
-   Fourniture des services critiques en vue de VSPackages externe.  
  
-   Fournissant une interface programmable, qui permet de participer à des éléments standard d'interface utilisateur.  
  
-   Créant des instances de VSPackages requis par l'objet identity des actions utilisateur ou d'autres services demande de VSPackages.  
  
-   Fournit des services qui rendent possible pour la communication et la coordination entre les VSPackages.  
  
-   Gestion de solutions et leurs fichiers requis.  
  
-   fourniture de la gestion des fenêtres.  
  
-   Fournissant le routage des commandes et les barres de commandes, telles que des menus, barres d'outils, et des menus contextuels.  
  
-   Sélection, contexte, et les devises coordonnés.  
  
 VSPackages sont responsable des tâches suivantes :  
  
-   effectuer certaines routines d'initialisation et d'arrêt.  
  
-   Les informations d'écriture dans le Registre, que l'IDE utilise pour charger le VSPackages approprié aux temps appropriés.  
  
-   Offrant les services requis pour communiquer avec l'autre des VSPackages.  
  
-   Fourniture des implémentations pour les nouveaux types, éditeurs, et concepteurs de projet.  
  
-   Fournissant des extensions pour les éléments prédéfinis d'interface utilisateur, tels que des tâches, des éléments de boîte à outils, et la boîte de dialogue options.  
  
## Voir aussi  
 [Shell Visual Studio](../extensibility/internals/visual-studio-shell.md)   
 [Packages VS](../extensibility/internals/vspackages.md)   
 [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md)