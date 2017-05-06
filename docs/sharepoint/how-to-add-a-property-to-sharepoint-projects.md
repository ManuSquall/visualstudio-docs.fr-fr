---
title: "How to: Add a Property to SharePoint Projects"
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
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Property to SharePoint Projects
  Vous pouvez utiliser une extension de projet pour ajouter une propriété à tout projet SharePoint.  La propriété s'affiche dans la fenêtre **Propriétés** lorsque le projet est sélectionné dans l'**Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension de projet.  Pour plus d'informations, consultez [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Pour ajouter une propriété à un projet SharePoint  
  
1.  Définissez une classe avec une propriété publique représentant la propriété que vous ajoutez à des projets SharePoint.  Pour ajouter plusieurs propriétés, vous pouvez définir toutes les propriétés dans la même classe ou dans des classes différentes.  
  
2.  Dans la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> de votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> du paramètre *projectService*.  
  
3.  Dans le gestionnaire d'événements de l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, ajoutez une instance de votre classe de propriétés à la collection <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> du paramètre d'arguments d'événement.  
  
## Exemple  
 L'exemple de code suivant montre comment ajouter deux propriétés à des projets SharePoint.  Une propriété rend ses données persistantes dans le fichier d'options utilisateur du projet \(fichier .csproj.user ou .vbproj.user\).  L'autre propriété rend ses données persistantes dans le fichier projet \(fichier .csproj ou .vbproj\).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#1)]
 [!code-vb[SpExt_SPCustomPrjProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#1)]  
  
### Fonctionnement du code  
 Pour garantir que la même instance de la classe `CustomProjectProperties` est utilisée chaque fois que l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> a lieu, l'exemple de code ajoute l'objet de propriétés dans la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> du projet la première fois que cet événement se produit.  Le code extrait cet objet chaque fois que cet événement se produit à nouveau.  Pour plus d'informations sur l'utilisation de la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> afin d'associer les données aux projets, consultez [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Pour rendre persistantes les modifications apportées aux valeurs de propriété, les accesseurs **set** des propriétés utilisent les API suivantes :  
  
-   `CustomUserFileProperty` utilise la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> pour sauvegarder sa valeur dans le fichier d'options utilisateur du projet.  
  
-   `CustomProjectFileProperty` utilise la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> pour sauvegarder sa valeur dans le fichier projet.  
  
 Pour plus d'informations sur la manière de rendre des données de ces fichiers persistantes, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Spécification du comportement des propriétés personnalisées  
 Vous pouvez définir la manière dont une propriété personnalisée apparaît et se comporte dans la fenêtre **Propriétés** en appliquant des attributs de l'espace de noms <xref:System.ComponentModel> à la définition de la propriété.  Les attributs suivants sont utiles dans de nombreux scénarios :  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> : spécifie le nom de la propriété qui s'affiche dans la fenêtre **Propriétés**.  
  
-   <xref:System.ComponentModel.DescriptionAttribute> : spécifie la chaîne de description qui s'affiche en bas de la fenêtre **Propriétés** lorsque la propriété est sélectionnée.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute> : spécifie la valeur par défaut de la propriété.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute> : spécifie une conversion personnalisée entre la chaîne affichée dans la fenêtre **Propriétés** et une valeur de propriété non\-chaîne.  
  
-   <xref:System.ComponentModel.EditorAttribute> : spécifie un éditeur personnalisé à utiliser pour modifier la propriété.  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  