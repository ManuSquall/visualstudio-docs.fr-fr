---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  Lorsque vous définissez un type d'élément de projet SharePoint personnalisé, vous pouvez ajouter un élément de menu contextuel à l'élément de projet.  L'élément de menu apparaît lorsqu'un utilisateur clique avec le bouton droit sur l'élément de projet dans l'**Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà défini votre propre type d'élément de projet SharePoint.  Pour plus d’informations, consultez [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Pour ajouter un élément de menu contextuel à un type d'élément de projet personnalisé  
  
1.  Dans la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> de votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> du paramètre *projectItemTypeDefinition*.  
  
2.  Dans votre gestionnaire d'événements pour l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>, ajoutez un nouvel objet <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> à la collection <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> du paramètre d'arguments d'événement.  
  
3.  Dans le gestionnaire d'événements d' <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> pour le nouvel objet d' <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , effectuez les tâches que vous souhaitez exécuter lorsqu'un utilisateur sélectionne votre élément de menu contextuel.  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter un élément de menu contextuel à un type d'élément de projet personnalisé.  Lorsque l'utilisateur ouvre le menu contextuel de l'élément de projet dans **Explorateur de solutions** et choisit l'élément de menu **message d'Écriture dans la fenêtre Sortie** , Visual Studio affiche un message dans la fenêtre **Sortie** .  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message dans la fenêtre **Sortie**.  Pour plus d’informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilation du code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'élément de projet  
 Pour donner à d'autres développeurs la possibilité d'utiliser votre élément de projet, créez un modèle de projet ou un modèle d'élément de projet.  Pour plus d’informations, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Pour déployer l'élément de projet, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly, le modèle et tous les autres fichiers que vous voulez distribuer avec l'élément de projet.  Pour plus d’informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  