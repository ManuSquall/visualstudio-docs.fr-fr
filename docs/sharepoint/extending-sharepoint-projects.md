---
title: "Extending SharePoint Projects"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  Créez une extension de projet si vous comptez personnaliser les fonctionnalités d'un projet SharePoint au niveau du projet.  Par exemple, vous pouvez ajouter des propriétés de projet personnalisées ou répondre à des événements au niveau du projet qui sont déclenchés lorsque l'utilisateur développe une solution SharePoint dans Visual Studio.  
  
## Création d'extensions de projet  
 Pour étendre un élément de projet, générez un assembly d'extension Visual Studio qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Pour plus d’informations, consultez [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Lorsque vous créez une extension de projet, vous pouvez également ajouter les fonctionnalités suivantes aux projets SharePoint :  
  
-   Ajout d'un élément de menu contextuel.  L'élément de menu apparaît lorsque vous ouvrez le menu contextuel pour un nœud de projet SharePoint dans **Explorateur de solutions** en cliquant avec le bouton droit sur le nœud ou en choisissant puis choisissez le décalage \+ les touches F10.  Pour plus d’informations, consultez [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Ajout d'une propriété personnalisée.  La propriété apparaît dans la fenêtre **Propriétés** lorsque vous sélectionnez un projet SharePoint dans **Explorateur de solutions**.  Pour plus d’informations, consultez [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Pour apprendre à créer, déployer et tester une extension de projet, étape par étape, consultez [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## Fonctionnement de la relation entre les extensions et les instances de projet  
 Lorsque vous créez une extension de projet, celle\-ci est chargée lors de l'ouverture de tout genre de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclut plusieurs modèles de projet SharePoint, tels que les définitions de listes, les types de contenu et les récepteurs d'événements.  Toutefois, il n'existe qu'un seul type de projet SharePoint.  Les types de projet figurant dans la boîte de dialogue **Nouveau projet** sont uniquement des modèles qui regroupent un ou plusieurs éléments de projet SharePoint.  Dans la mesure où il n'existe qu'un seul type de projet SharePoint, les extensions créées pour un projet s'appliquent à tous les projets SharePoint.  Par exemple, vous ne pouvez pas créer d'extension s'appliquant à un seul projet **Type de contenu**.  
  
 Pour accéder à une instance de projet spécifique, gérez l'un des événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> du paramètre *projectService* dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  Par exemple, pour déterminer quand un projet SharePoint est ajouté à une solution, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>.  Pour plus d’informations, consultez [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Voir aussi  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  