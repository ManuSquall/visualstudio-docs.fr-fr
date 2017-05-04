---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects | Microsoft Docs"
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  Vous pouvez ajouter un élément de menu contextuel à tout projet SharePoint.  L'élément de menu apparaît lorsqu'un utilisateur clique avec le bouton droit sur un nœud de projet dans l'**Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension de projet.  Pour plus d'informations, consultez [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Pour ajouter un élément de menu contextuel à des projets SharePoint  
  
1.  Dans la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> de votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> du paramètre *projectService*.  
  
2.  Dans votre gestionnaire d'événements pour l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>, ajoutez un nouvel objet <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> à la collection <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> du paramètre d'arguments d'événement.  
  
3.  Dans le gestionnaire d'événements <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> pour le nouvel objet <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>, effectuez les tâches que vous voulez exécuter lorsqu'un utilisateur clique sur votre élément de menu contextuel.  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter un élément de menu contextuel aux nœuds de projet SharePoint dans l'**Explorateur de solutions**.  Lorsque l'utilisateur clique avec le bouton droit sur un nœud de projet, puis clique sur l'élément de menu **Écrire le message dans la fenêtre Sortie**, Visual Studio affiche un message dans la fenêtre **Sortie**.  Cet exemple utilise le service de projet SharePoint pour afficher le message.  Pour plus d'informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## Compilation du code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  