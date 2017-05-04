---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  Vous pouvez ajouter un élément de menu contextuel à un élément de projet SharePoint existant à l'aide d'une extension d'élément de projet.  L'élément de menu apparaît lorsqu'un utilisateur clique avec le bouton droit sur l'élément de projet dans l'**Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension d'élément de projet.  Pour plus d'informations, consultez [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Pour ajouter un élément de menu contextuel dans une extension d'élément de projet  
  
1.  Dans la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> de votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> du paramètre *projectItemType*.  
  
2.  Dans votre gestionnaire d'événements pour l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>, ajoutez un nouvel objet <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> à la collection <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> du paramètre d'arguments d'événement.  
  
3.  Dans le gestionnaire d'événements <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> pour le nouvel objet <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>, effectuez les tâches que vous voulez exécuter lorsqu'un utilisateur clique sur votre élément de menu contextuel.  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter un élément de menu contextuel à l'élément de projet Récepteur d'événements.  Lorsque l'utilisateur clique avec le bouton droit sur l'élément de projet dans l'**Explorateur de solutions**, puis clique sur l'élément de menu **Écrire le message dans la fenêtre Sortie**, Visual Studio affiche un message dans la fenêtre **Sortie**.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message dans la fenêtre **Sortie**.  Pour plus d'informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilation du code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  