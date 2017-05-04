---
title: "How to: Add a Property to a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# How to: Add a Property to a SharePoint Project Item Extension
  Vous pouvez utiliser une extension d'élément de projet pour ajouter une propriété à un élément de projet SharePoint déjà installé dans Visual Studio.  La propriété apparaît dans la fenêtre **Propriétés** dès lors que l'élément de projet est sélectionné dans l'**Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension d'élément de projet.  Pour plus d'informations, consultez [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Comment : ajouter une propriété à une extension d'élément de projet  
  
1.  Définissez une classe avec une propriété publique représentant la propriété que vous ajoutez à un type d'élément de projet.  Pour ajouter plusieurs propriétés à un type d'élément de projet, vous pouvez définir toutes les propriétés dans la même classe ou dans des classes différentes.  
  
2.  Dans la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> de votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> du paramètre *projectItemType*.  
  
3.  Dans le gestionnaire d'événements de l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, ajoutez une instance de votre classe de propriétés à la collection <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> du paramètre d'arguments d'événement.  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter une propriété nommée **Example Property** \(Exemple de propriété\) à l'élément de projet Récepteur d'événements.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionproperty.vb#8)]  
  
### Fonctionnement du code  
 Pour garantir que la même instance de la classe `CustomProperties` est utilisée chaque fois que l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> a lieu, l'exemple de code ajoute l'objet de propriétés dans la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de l'élément de projet la première fois que cet événement se produit.  Le code extrait cet objet chaque fois que cet événement se produit à nouveau.  Pour plus d'informations sur l'utilisation de la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> afin d'associer les données aux éléments de projet, consultez [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Pour rendre persistantes les modifications apportées à la valeur de propriété, l'accesseur **set** pour `ExampleProperty` enregistre la nouvelle valeur dans la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> de l'objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> auquel la propriété est associée.  Pour plus d'informations sur l'utilisation de la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> afin de rendre persistantes les données avec les éléments de projet, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Spécification du comportement des propriétés personnalisées  
 Vous pouvez définir la manière dont une propriété personnalisée apparaît et se comporte dans la fenêtre **Propriétés** en appliquant des attributs de l'espace de noms <xref:System.ComponentModel> à la définition de la propriété.  Les attributs suivants sont utiles dans de nombreux scénarios :  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> : spécifie le nom de la propriété qui s'affiche dans la fenêtre **Propriétés**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> : spécifie la chaîne de description qui s'affiche en bas de la fenêtre **Propriétés** lorsque la propriété est sélectionnée.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> : spécifie la valeur par défaut de la propriété.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute> : spécifie une conversion personnalisée entre la chaîne affichée dans la fenêtre **Propriétés** et une valeur de propriété non\-chaîne.  
  
-   <xref:System.ComponentModel.EditorAttribute> : spécifie un éditeur personnalisé à utiliser pour modifier la propriété.  
  
## Compilation du code  
 Ces exemples requièrent un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  