---
title: "Associating Custom Data with SharePoint Tools Extensions | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  Vous pouvez ajouter des données personnalisées à certains objets dans les extensions d'outils SharePoint.  Cela est utile lorsque vous possédez des données dans une partie de votre extension auxquelles vous souhaitez accéder ultérieurement à partir d'un autre code dans votre extension.  Au lieu d'implémenter une manière personnalisée de stocker et d'accéder aux données, vous pouvez associer les données à un objet dans votre extension, puis extraire ultérieurement les données à partir de cet objet.  
  
 L'ajout de données personnalisées aux objets est également utile lorsque vous souhaitez conserver des données qui s'appliquent uniquement à un élément spécifique dans Visual Studio.  Les extensions d'outils SharePoint n'étant chargées qu'une seule fois dans Visual Studio, votre extension peut fonctionner n'importe quand avec plusieurs éléments différents \(tels que des projets, des éléments de projet ou des nœuds **Server Explorer**\).  Si vous possédez des données personnalisées qui s'appliquent uniquement à un élément spécifique, vous pouvez ajouter ces données à l'objet représentant cet élément.  
  
 Lorsque vous ajoutez des données personnalisées aux objets dans les extensions d'outils SharePoint, les données ne sont pas persistantes.  Les données sont disponibles uniquement au cours de la durée de vie de l'objet.  Une fois que l'objet a été récupéré par une opération garbage collection, les données sont perdues.  
  
 Dans les extensions du système de projet SharePoint, vous pouvez également enregistrer des données de type chaîne qui persistent après le déchargement d'une extension.  Pour plus d'informations, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Objets pouvant contenir des données personnalisées  
 Vous pouvez ajouter des données personnalisées à tout objet du modèle d'objet Outils SharePoint qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Cette interface définit une seule propriété, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, qui représente une collection d'objets de données personnalisés.  Les types suivants implémentent <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## Ajout et extraction de données personnalisées  
 Pour ajouter des données personnalisées à un objet dans une extension d'outils SharePoint, obtenez la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de l'objet auquel vous souhaitez ajouter les données, puis utilisez la méthode <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> pour ajouter les données à l'objet.  
  
 Pour récupérer des données personnalisées d'un objet dans une extension d'outils SharePoint, obtenez la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de l'objet, puis utilisez l'une des méthodes suivantes :  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  Cette méthode retourne **true** si l'objet de données existe et **false** s'il n'existe pas.  Vous pouvez utiliser cette méthode pour récupérer des instances de type valeur ou de type référence.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  Cette méthode retourne l'objet de données s'il existe et **null** s'il n'existe pas.  Vous pouvez utiliser cette méthode uniquement pour récupérer des instances de type référence.  
  
 L'exemple de code suivant détermine si un objet de données est déjà associé à un élément de projet.  Si l'objet de données n'est pas déjà associé à l'élément de projet, le code ajoute l'objet à la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de l'élément de projet.  Pour voir cet exemple dans un contexte plus large, consultez [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## Voir aussi  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  