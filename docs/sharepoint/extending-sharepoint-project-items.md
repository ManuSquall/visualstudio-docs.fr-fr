---
title: Extension d’éléments de projet SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f60c95418379399196c461e055645ae7c85a473e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967394"
---
# <a name="extend-sharepoint-project-items"></a>Étendre des éléments de projet SharePoint
  Créer une extension d’élément de projet lorsque vous souhaitez ajouter des fonctionnalités à un type d’élément de projet SharePoint qui est déjà installé dans Visual Studio. Par exemple, vous pouvez créer une extension pour intégrés **récepteur d’événements** ou **définition de liste** les éléments de projet dans Visual Studio, ou vous pouvez créer une extension pour un type d’élément de projet personnalisé. Vous pouvez également créer une extension pour tous les types d’éléments de projet SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Tâches permettant d’étendre les éléments de projet SharePoint
 Pour étendre un élément de projet, créez un assembly d’extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Pour plus d'informations, voir [Procédure : Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Lorsque vous étendez un élément de projet, vous pouvez également ajouter les fonctionnalités suivantes à l’élément de projet :

- Ajouter un élément de menu contextuel à l’élément de projet. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel de l’élément de projet dans **l’Explorateur de solutions**. Vous ouvrez le menu contextuel en cliquant sur l’élément de projet ou en sélectionnant puis en choisissant le **MAJ**+**F10** clés. Pour plus d'informations, voir [Procédure : Ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Ajouter une propriété personnalisée à l’élément de projet. La propriété apparaît dans le **propriétés** fenêtre lorsque vous choisissez l’élément de projet dans **l’Explorateur de solutions**. Pour plus d'informations, voir [Procédure : Ajouter une propriété à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Pour une procédure pas à pas qui montre comment créer, déployer et tester une extension d’élément de projet, consultez [procédure pas à pas : Étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Comprendre la relation entre les extensions d’élément de projet et les instances d’élément de projet
 Lorsque vous créez une extension d’élément de projet, Visual Studio charge votre extension lors de l’ajout d’un élément de projet du type associé à un projet SharePoint. Par exemple, si vous créez une extension pour **récepteur d’événements** des éléments de projet, Visual Studio charge votre extension lorsqu’un utilisateur ajoute un **récepteur d’événements** élément de projet à un projet. Visual Studio utilise la même instance de votre extension pour toutes les instances du type d’élément de projet associé. Dans l’exemple précédent, si l’utilisateur ajoute un deuxième **récepteur d’événements** l’élément de projet au projet, la même instance de votre extension est utilisée pour personnaliser le deuxième élément de projet.

 Pour accéder à une instance spécifique du type d’élément de projet que vous étendez, gérez l’un de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements de la *projectItemType* paramètre dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> (méthode). Par exemple, pour déterminer quand un élément de projet du type que vous étendez est ajouté à un projet, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> événement. Pour plus d'informations, voir [Procédure : Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identificateurs pour les éléments de projet SharePoint
 Chaque élément de projet SharePoint a un identificateur de chaîne. Vous devez connaître l’identificateur pour un élément de projet si vous souhaitez effectuer les tâches suivantes :

- Créer une extension pour l’élément de projet. Dans ce cas, vous devez passer l’identificateur de l’élément de projet que vous souhaitez étendre au constructeur de la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Pour créer une extension pour tous les types de projet élément, transmettez le **\\*** valeur de chaîne.

- Ajouter l’élément de projet à un projet par programmation. Dans ce cas, vous devez passer l’identificateur pour l’élément de projet à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> (méthode).

  Le tableau suivant répertorie les identificateurs pour les éléments de projet SharePoint qui sont inclus avec Visual Studio.

|Nom d’élément de projet|Identificateur de chaîne|
|-----------------------|-----------------------|
|Modèle de catalogue de données métiers|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|
|Type de contenu|Microsoft.VisualStudio.SharePoint.ContentType|
|Récepteur d’événements|Microsoft.VisualStudio.SharePoint.EventHandler|
|Élément vide|Microsoft.VisualStudio.SharePoint.GenericElement|
|Définition de liste<br /><br /> Définition de liste à partir du Type de contenu|Microsoft.VisualStudio.SharePoint.ListDefinition|
|Instance de liste|Microsoft.VisualStudio.SharePoint.ListInstance|
|Module|Microsoft.VisualStudio.SharePoint.Module|
|Flux de travail séquentiel<br /><br /> Flux de travail de l'ordinateur d'état|Microsoft.VisualStudio.SharePoint.Workflow|
|Définition de site|Microsoft.VisualStudio.SharePoint.SiteDefinition|
|Composant Visual Web Part|Microsoft.VisualStudio.SharePoint.VisualWebPart|
|Composant Web Part|Microsoft.VisualStudio.SharePoint.WebPart|
|Formulaire d’Association de flux de travail|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Guide pratique pour Ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Guide pratique pour Ajouter une propriété à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Procédure pas à pas : Étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
