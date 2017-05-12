---
title: "How to: Create a SharePoint Project Extension"
ms.custom: ""
ms.date: "04/28/2017"
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
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  Créez une extension de projet si vous avez l'intention d'ajouter une fonctionnalité à un projet SharePoint ouvert dans Visual Studio.  Pour plus d'informations, consultez [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Pour créer une extension de projet  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  
  
4.  Ajoutez l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe.  Cet attribut permet à Visual Studio de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Passez le type <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> au constructeur d'attribut.  
  
5.  Dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>, utilisez les membres du paramètre *projectService* pour définir le comportement de votre extension.  Ce paramètre est un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> qui fournit l'accès aux événements définis dans l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  
  
## Exemple  
 L'exemple de code suivant montre comment créer une extension de projet simple qui gère la plupart des événements de projet SharePoint définis par l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  Pour tester le code, créez un projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], puis ajoutez d'autres projets à la solution, modifiez les valeurs de propriété du projet, ou supprimez ou excluez un projet.  L'extension vous informe des événements en écrivant des messages dans les fenêtres **Sortie** et **Liste d'erreurs**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message dans les fenêtres **Sortie** et **Liste d'erreurs**.  Pour plus d'informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Pour obtenir des exemples illustrant la gestion des événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, consultez [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) et [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  