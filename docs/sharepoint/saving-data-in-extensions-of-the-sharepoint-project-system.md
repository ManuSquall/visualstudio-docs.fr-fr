---
title: "Saving Data in Extensions of the SharePoint Project System"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  Lorsque vous étendez le système de projet SharePoint, vous pouvez enregistrer des données de type chaîne qui persistent après la fermeture d'un projet SharePoint.  Les données sont généralement associées à un élément de projet particulier ou au projet lui\-même.  
  
 Si vous disposez de données qui ne doivent pas nécessairement persister, vous pouvez ajouter les données à n'importe quel objet du modèle d'objet d'outils SharePoint qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Pour plus d'informations, consultez [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Enregistrement des données associées à un élément de projet  
 Lorsque vous avez données qui sont associées à un élément de projet SharePoint particulier, par exemple la valeur d'une propriété que vous ajoutez à un élément de projet, vous pouvez enregistrer les données dans le fichier .spdata pour l'élément de projet.  Pour ce faire, utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>.  Les données que vous ajoutez à cette propriété sont enregistrées dans l'élément **ExtensionData** dans le fichier .spdata de l'élément de projet.  Pour plus d'informations, consultez [ExtensionData Element](../sharepoint/extensiondata-element.md).  
  
 L'exemple de code suivant montre comment utiliser la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> pour enregistrer la valeur d'une propriété de type chaîne définie dans un type d'élément de projet SharePoint personnalisé.  Pour voir cet exemple dans un contexte plus large, consultez [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## Enregistrement des données associées à un projet  
 Lorsque vous avez des données au niveau du projet, comme la valeur d'une propriété que vous ajoutez à des projets SharePoint, vous pouvez enregistrer les données dans le fichier projet \(fichier .csproj ou .vbproj\) ou le fichier d'options utilisateur du projet \(fichier .csproj.user ou .vbproj.user\).  Le fichier dans lequel vous choisissez d'enregistrer les données dépend du mode d'utilisation des données :  
  
-   Si vous souhaitez mettre les données à la disposition de tous les développeurs qui ouvrent le projet SharePoint, enregistrez les données dans le fichier projet.  Comme ce fichier est toujours archivé dans les bases de données du contrôle de code source, ses données sont à la disposition d'autres développeurs qui extraient le projet.  
  
-   Si vous souhaitez que les données soient disponibles uniquement au développeur en cours qui a ouvert le projet SharePoint dans Visual Studio, enregistrez les données dans le fichier d'options utilisateur du projet.  Comme ce fichier n'est pas toujours archivé dans les bases de données du contrôle de code source, ses données ne sont pas à la disposition d'autres développeurs qui extraient le projet.  
  
### Enregistrement des données dans le fichier projet  
 Pour enregistrer des données dans le fichier projet, convertissez un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>, puis utilisez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>.  L'exemple de code suivant illustre le mode d'utilisation de cette méthode pour enregistrer la valeur d'une propriété de projet dans le fichier projet.  Pour voir cet exemple dans un contexte plus large, consultez [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 Pour plus d'informations sur la conversion des objets <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en types différents dans le modèle d'objet Automation de Visual Studio ou dans le modèle d'objet Intégration, consultez [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### Enregistrement des données dans le fichier d'options utilisateur du projet  
 Pour enregistrer des données dans le fichier d'options utilisateur du projet, utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  L'exemple de code suivant illustre le mode d'utilisation de cette propriété pour enregistrer la valeur d'une propriété de projet dans le fichier d'options utilisateur du projet.  Pour voir cet exemple dans un contexte plus large, consultez [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## Voir aussi  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  