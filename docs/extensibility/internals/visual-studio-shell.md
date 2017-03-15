---
title: "Shell Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell, Visual Studio"
  - "Visual Studio shell"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Shell Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell est l’agent principal d’intégration [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Le shell fournit les fonctionnalités nécessaires pour activer les packages VS partager des services communs. Étant donné que l’objectif architectural de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est à l’exercice des fonctionnalités principales dans les packages VS, l’interpréteur de commandes est une infrastructure pour fournir des fonctionnalités de base et prennent en charge les communications entre son composant VSPackages.  
  
## Responsabilités de l’interpréteur de commandes  
 L’interpréteur de commandes a les responsabilités principales suivantes :  
  
-   Prise en charge des éléments de l’interface utilisateur \(IU\) de base \(par le biais des interfaces COM\). Notamment, les menus par défaut et barres d’outils, les cadres de fenêtres de document ou windows d’enfant d’interface multidocument \(MDI\) et des cadres de fenêtre outil et prise en charge d’ancrage.  
  
-   Maintenir une liste de tous les documents actuellement ouverts dans une table de documents en cours d’exécution \(r & DT\) afin de coordonner la persistance des documents et de garantir qu’un document ne peut pas être ouvert dans plusieurs différentes façons, ou comme incompatible.  
  
-   Prise en charge de l’interface de commande et de la gestion des commandes, `IOleCommandTarget`.  
  
-   Chargement des packages VS aux moments opportuns. Le chargement différé un VSPackage est nécessaire pour améliorer les performances de l’interpréteur de commandes.  
  
-   La gestion de certains des services partagés, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, qui fournit des fonctionnalités de l’interface de base, et <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui fournit des fonctionnalités de base de fenêtrage.  
  
-   Gestion des fichiers solution \(.sln\). Les solutions contiennent des groupes de projets connexes, semblables aux fichiers de l’espace de travail \(.dsw\) dans Visual C\+\+ 6.0.  
  
-   Sélection du suivi au niveau du shell, contexte et des devises. L’interpréteur de commandes effectue le suivi des éléments suivants :  
  
    -   Le projet actuel  
  
    -   L’élément de projet en cours ou ItemID actuel <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La sélection actuelle pour le **propriétés** fenêtre ou `SelectionContainer`  
  
    -   Le contexte de l’interface utilisateur, ID ou CmdUIGuids qui contrôlent la visibilité des commandes, des menus et barres d’outils  
  
    -   Les éléments actuellement actifs tels que la fenêtre active, le document et le Gestionnaire d’annulation  
  
    -   Les attributs de contexte de l’utilisateur qui définissent l’aide dynamique  
  
 L’interpréteur de commandes gère également la communication entre les VSPackages installés et les services en cours. Il prend en charge les fonctionnalités principales de l’interpréteur de commandes et les rend disponibles pour tous les packages VS intégrés dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ces fonctionnalités incluent les éléments suivants :  
  
-   **Sur** écran de démarrage et la boîte de dialogue  
  
-   **Nouveau et ajouter un élément existant** boîtes de dialogue  
  
-   **Affichage de classes** fenêtre et **Explorateur d’objets**  
  
-   **Références** boîte de dialogue  
  
-   **Structure du document** fenêtre  
  
-   **Aide dynamique** fenêtre  
  
-   **Trouver** et **remplacer**  
  
-   **Ouvrir un projet** et **Ouvrir le fichier** boîtes de dialogue sur le **nouveau** menu  
  
-   **Options** boîte de dialogue sur le **outils** menu  
  
-   **Propriétés** fenêtre  
  
-   **Explorateur de solutions**  
  
-   **Liste des tâches** fenêtre  
  
-   **Boîte à outils**  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [Packages VS](../../extensibility/internals/vspackages.md)