---
title: "Extending SharePoint Project Items"
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
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  Créez une extension d'élément de projet si vous avez l'intention d'ajouter des fonctionnalités à un type d'élément de projet SharePoint déjà installé dans Visual Studio.  Par exemple, vous pouvez créer une extension pour les éléments de projet **Récepteur d'événements** ou **Définition de liste** intégrés dans Visual Studio, ou pour un type d'élément de projet personnalisé.  Vous avez également la possibilité de créer une extension pour tous les types d'éléments de projet SharePoint.  
  
## Tâches permettant d'étendre les éléments de projet SharePoint  
 Pour étendre un élément de projet, générez un assembly d'extension Visual Studio qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Pour plus d’informations, consultez [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Lorsque vous étendez un élément de projet, vous pouvez également ajouter les fonctionnalités suivantes à l'élément de projet :  
  
-   Ajout d'un élément de menu contextuel à l'élément de projet.  L'élément de menu apparaît lorsque vous ouvrez le menu contextuel pour l'élément de projet dans **Explorateur de solutions**.  Ouvrez le menu contextuel en cliquant avec le bouton droit sur l'élément de projet ou en choisissant puis choisissez le décalage \+ les touches F10.  Pour plus d’informations, consultez [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Ajout d'une propriété personnalisée à l'élément de projet.  La propriété apparaît dans la fenêtre **Propriétés** lorsque vous sélectionnez l'élément de projet dans **Explorateur de solutions**.  Pour plus d’informations, consultez [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Pour apprendre à créer, déployer et tester une extension d'élément de projet, étape par étape, consultez [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## Fonctionnement de la relation entre les extensions et les instances d'éléments de projet  
 Lorsque vous créez une extension d'élément de projet, Visual Studio charge votre extension au moment où un élément de projet du type associé est ajouté à un projet SharePoint.  Par exemple, si vous créez une extension pour les éléments de projet **Récepteur d'événements**, Visual Studio charge votre extension lorsqu'un utilisateur ajoute un élément de projet **Récepteur d'événements** à un projet.  Visual Studio utilise la même instance de votre extension pour toutes les instances du type d'élément de projet associé.  Dans l'exemple précédent, si l'utilisateur ajoute un deuxième élément de projet **Récepteur d'événements** au projet, la même instance de votre extension est employée pour personnaliser le deuxième élément de projet.  
  
 Pour accéder à une instance spécifique du type d'élément de projet que vous étendez, gérez l'un des événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> du paramètre *projectItemType* dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  Par exemple, pour déterminer quand un élément de projet du type que vous étendez est ajouté à un projet, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Pour plus d’informations, consultez [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## Identificateurs pour les éléments de projet SharePoint  
 Chaque élément de projet SharePoint est défini par un identificateur de chaîne.  Vous devez impérativement connaître l'identificateur d'un élément de projet pour effectuer les tâches suivantes :  
  
-   Créer une extension pour l'élément de projet.  Dans ce cas, vous devez passer l'identificateur de l'élément de projet que vous voulez étendre au constructeur de <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Pour créer une extension pour tous les types d'éléments de projet, passez la valeur de chaîne **\***.  
  
-   Ajouter un élément de projet à un projet par programmation.  Dans ce cas, vous devez communiquer l'identificateur de l'élément de projet à la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>.  
  
 Le tableau suivant répertorie les identificateurs des éléments de projet SharePoint inclus avec Visual Studio.  
  
|Nom d'élément de projet|Identificateur de chaîne|  
|-----------------------------|------------------------------|  
|Modèle de catalogue de données métiers|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Content\-Type|Microsoft.VisualStudio.SharePoint.ContentType|  
|Récepteur d'événements|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Élément vide|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Définition de liste<br /><br /> Definition de liste du type de contenu|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Instance de liste|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Module|Microsoft.VisualStudio.SharePoint.Module|  
|Workflow séquentiel<br /><br /> Flux de travail de la machine à états|Microsoft.VisualStudio.SharePoint.Workflow|  
|Définition de site|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Composant Visual Web Part|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Composant Web Part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formulaire d'association de flux de travail|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## Voir aussi  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  