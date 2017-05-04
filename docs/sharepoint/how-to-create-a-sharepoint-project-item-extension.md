---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  Créez une extension d'élément de projet si vous avez l'intention d'ajouter des fonctionnalités à un élément de projet SharePoint déjà installé dans Visual Studio.  Pour plus d'informations, consultez [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
### Pour créer une extension d'élément de projet  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Ajouter les attributs suivants à la classe :  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Cet attribut permet à Visual Studio de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Communiquez le type <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> au constructeur d'attribut.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Dans une extension d'élément de projet, cet attribut identifie l'élément de projet que vous souhaitez étendre.  Passez l'ID de l'élément de projet au constructeur d'attribut.  Pour obtenir la liste des ID des éléments de projet qui sont inclus dans Visual Studio, consultez [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  Dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>, utilisez les membres du paramètre *projectItemType* pour définir le comportement de votre extension.  Ce paramètre est un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> qui fournit l'accès aux événements définis dans les interfaces <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Pour accéder à une instance spécifique du type d'élément de projet que vous étendez, gérez les événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> tels que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Exemple  
 L'exemple de code suivant montre comment créer une extension simple pour l'élément de projet Récepteur d'événements.  Chaque fois que l'utilisateur ajoute un élément de projet Récepteur d'événements à un projet SharePoint, cette extension écrit un message dans les fenêtres **Sortie** et **Liste d'erreurs**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message dans les fenêtres **Sortie** et **Liste d'erreurs**.  Pour plus d'informations, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  