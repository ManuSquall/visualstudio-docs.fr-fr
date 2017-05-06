---
title: "How to: Add a Property to a Custom SharePoint Project Item Type"
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
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Add a Property to a Custom SharePoint Project Item Type
  Lorsque vous définissez un type d'élément de projet SharePoint personnalisé, vous pouvez ajouter une propriété à l'élément de projet.  La propriété apparaît dans la fenêtre **Propriétés** dès lors que l'élément de projet est sélectionné dans l'**Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà défini votre propre type d'élément de projet SharePoint.  Pour plus d'informations, consultez [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Pour ajouter une propriété à une définition d'un type d'élément de projet  
  
1.  Définissez une classe avec une propriété publique représentant la propriété que vous ajoutez au type d'élément de projet personnalisé.  Si vous voulez ajouter plusieurs propriétés à un type d'élément de projet personnalisé, vous pouvez définir toutes les propriétés dans la même classe ou dans différentes classes.  
  
2.  Dans la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> de votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> du paramètre *projectItemTypeDefinition*.  
  
3.  Dans le gestionnaire d'événements de l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested>, ajoutez une instance de votre classe de propriétés personnalisées à la collection <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> du paramètre d'arguments d'événement.  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter une propriété nommée **Example Property** \(Exemple de propriété\) à un type d'élément de projet personnalisé.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#11)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#11)]  
  
### Fonctionnement du code  
 Pour garantir que la même instance de la classe `CustomProperties` est utilisée chaque fois que l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> a lieu, l'exemple de code enregistre l'objet de propriétés dans la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de l'élément de projet la première fois que cet événement se produit.  Le code extrait cet objet chaque fois que cet événement se produit à nouveau.  Pour plus d'informations sur l'utilisation de la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> afin d'enregistrer des données avec des éléments de projet, consultez [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Pour rendre persistantes les modifications apportées à la valeur de propriété, l'accesseur **set** pour `ExampleProperty` enregistre la nouvelle valeur dans la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> de l'objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> auquel la propriété est associée.  Pour plus d'informations sur l'utilisation de la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> afin de rendre persistantes les données avec les éléments de projet, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Spécification du comportement des propriétés personnalisées  
 Vous pouvez définir la manière dont une propriété personnalisée apparaît et se comporte dans la fenêtre **Propriétés** en appliquant des attributs de l'espace de noms <xref:System.ComponentModel> à la définition de la propriété.  Les attributs suivants sont utiles dans de nombreux scénarios :  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> : spécifie le nom de la propriété qui s'affiche dans la fenêtre **Propriétés**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> : spécifie la chaîne de description qui s'affiche en bas de la fenêtre **Propriétés** lorsque la propriété est sélectionnée.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> : spécifie la valeur par défaut de la propriété.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute> : spécifie une conversion personnalisée entre la chaîne affichée dans la fenêtre **Propriétés** et une valeur de propriété non\-chaîne.  
  
-   <xref:System.ComponentModel.EditorAttribute> : spécifie un éditeur personnalisé à utiliser pour modifier la propriété.  
  
## Compilation du code  
 Ces exemples de code requièrent un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'élément de projet  
 Pour donner à d'autres développeurs la possibilité d'utiliser votre élément de projet, créez un modèle de projet ou un modèle d'élément de projet.  Pour plus d'informations, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Pour déployer l'élément de projet, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly, le modèle et tous les autres fichiers que vous voulez distribuer avec l'élément de projet.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  