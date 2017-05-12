---
title: "Defining Custom SharePoint Project Item Types"
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
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  Définissez un type d'élément de projet SharePoint si vous voulez créer un nouveau genre d'élément de projet SharePoint.  Par exemple, Visual Studio n'inclut pas les éléments de projet SharePoint pour ajouter des champs ou des actions personnalisées à un site SharePoint.  Vous pouvez définir vos propres types d'éléments de projet SharePoint pour la création de champs, d'actions personnalisées ou d'autres types de composants SharePoint.  
  
## Tâches permettant de définir des types d'éléments de projet SharePoint  
 Pour définir un type d'élément de projet personnalisé, générez un assembly d'extension Visual Studio qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Pour plus d’informations, consultez [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Lorsque vous définissez un type d'élément de projet personnalisé, vous pouvez également ajouter les fonctionnalités suivantes à l'élément de projet :  
  
-   Ajout d'un élément de menu contextuel à l'élément de projet.  L'élément de menu apparaît lorsque vous ouvrez le menu contextuel pour l'élément de projet dans **Explorateur de solutions** en cliquant avec le bouton droit sur l'élément de projet ou en choisissant puis choisissez le décalage \+ les touches F10.  Pour plus d’informations, consultez [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Ajout d'une propriété personnalisée à l'élément de projet.  La propriété apparaît dans la fenêtre **Propriétés** lorsque vous sélectionnez l'élément de projet dans **Explorateur de solutions**.  Pour plus d’informations, consultez [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Pour permettre à d'autres développeurs d'utiliser votre élément de projet dans Visual Studio, créez un fichier .spdata et un modèle d'élément ou de projet associé à l'élément de projet.  Pour plus d’informations, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Fonctionnement de la relation entre les types et les instances d'éléments de projet  
 Lorsque vous définissez un type d'élément de projet SharePoint, Visual Studio charge votre extension au moment où un élément de projet du type associé est ajouté à un projet SharePoint.  Par exemple, si vous définissez un nouveau type d'élément de projet **Action personnalisée**, Visual Studio charge votre extension lorsqu'un utilisateur ajoute un élément de projet **Action personnalisée** à un projet.  Visual Studio utilise la même instance de votre extension pour toutes les instances du type d'élément de projet associé.  Dans l'exemple précédent, si l'utilisateur ajoute un deuxième élément de projet **Action personnalisée** au projet, la même instance de votre extension est employée pour personnaliser le deuxième élément de projet.  
  
 Pour accéder à une instance spécifique de votre type d'élément de projet, gérez l'un des événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> du paramètre *projectItemTypeDefinition* dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Par exemple, pour déterminer quand un élément de projet de votre type personnalisé est ajouté à un projet, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Pour plus d’informations, consultez [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Voir aussi  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  