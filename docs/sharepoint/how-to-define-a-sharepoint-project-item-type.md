---
title: "How to: Define a SharePoint Project Item Type"
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
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  Définissez un type d'élément de projet si vous avez l'intention de créer un nouvel élément de projet SharePoint personnalisé.  Pour plus d’informations, consultez [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### Pour définir un type d'élément de projet  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Ajouter les attributs suivants à la classe :  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Cet attribut permet à Visual Studio de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Communiquez le type <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> au constructeur d'attribut.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Dans une définition de type d'élément de projet, cet attribut spécifie l'identificateur de chaîne pour le nouvel élément de projet.  Nous vous recommandons de respecter le format *NomSociété*.*NomFonctionnalité* pour vous assurer d'attribuer des noms uniques et cohérents à tous les éléments de projet.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  Cet attribut désigne l'icône utilisée pour représenter cet élément de projet dans l'**Explorateur de solutions**.  Cet attribut est facultatif ; si vous ne l'appliquez pas à votre classe, Visual Studio affiche une icône par défaut pour votre élément de projet.  Si vous définissez cet attribut, communiquez le nom qualifié complet d'une icône ou d'un fichier bitmap incorporé dans votre assembly.  
  
5.  Dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>, utilisez les membres du paramètre *projectItemTypeDefinition* pour définir le comportement du type d'élément de projet.  Ce paramètre est un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> qui fournit l'accès aux événements définis dans les interfaces <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Pour accéder à une instance spécifique de votre type d'élément de projet, gérez les événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> tels que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Exemple  
 L'exemple de code suivant montre comment définir un type d'élément de projet simple.  Ce type d'élément de projet écrit un message dans les fenêtres **Sortie** et **Liste d'erreurs** lorsqu'un utilisateur ajoute un élément de projet de ce type à un projet.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message dans les fenêtres **Sortie** et **Liste d'erreurs**.  Pour plus d’informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'élément de projet  
 Pour donner à d'autres développeurs la possibilité d'utiliser votre élément de projet, créez un modèle de projet ou un modèle d'élément de projet.  Pour plus d’informations, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Pour déployer l'élément de projet, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly, le modèle et tous les autres fichiers que vous voulez distribuer avec l'élément de projet.  Pour plus d’informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  