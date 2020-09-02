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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967394"
---
# <a name="extend-sharepoint-project-items"></a>Étendre les éléments de projet SharePoint
  Créez une extension d’élément de projet lorsque vous souhaitez ajouter des fonctionnalités à un type d’élément de projet SharePoint qui est déjà installé dans Visual Studio. Par exemple, vous pouvez créer une extension pour les éléments de projet de **récepteur d’événements** ou de définition de **liste** intégrés dans Visual Studio, ou vous pouvez créer une extension pour un type d’élément de projet personnalisé. Vous pouvez également créer une extension pour tous les types d’éléments de projet SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Tâches d’extension d’éléments de projet SharePoint
 Pour étendre un élément de projet, générez un assembly d’extension Visual Studio qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Pour plus d’informations, consultez [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Lorsque vous étendez un élément de projet, vous pouvez également ajouter les fonctionnalités suivantes à l’élément de projet :

- Ajoutez un élément de menu contextuel à l’élément de projet. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel de l’élément de projet dans **Explorateur de solutions**. Pour ouvrir le menu contextuel, cliquez avec le bouton droit sur l’élément de projet ou sélectionnez-le, puis appuyez sur les touches **MAJ** + **F10** . Pour plus d’informations, consultez [Comment : ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Ajoutez une propriété personnalisée à l’élément de projet. La propriété s’affiche dans la fenêtre **Propriétés** lorsque vous choisissez l’élément de projet dans **Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ajouter une propriété à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Pour obtenir une procédure pas à pas qui montre comment créer, déployer et tester une extension d’élément de projet, consultez [procédure pas à pas : étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Comprendre la relation entre les extensions d’élément de projet et les instances d’élément de projet
 Quand vous créez une extension d’élément de projet, Visual Studio charge votre extension lorsqu’un élément de projet du type associé est ajouté à un projet SharePoint. Par exemple, si vous créez une extension pour des éléments de projet de **récepteur d’événements** , Visual Studio charge votre extension quand un utilisateur ajoute un élément de projet de **récepteur d’événements** à un projet. Visual Studio utilise la même instance de votre extension pour toutes les instances du type d’élément de projet associé. Dans l’exemple précédent, si l’utilisateur ajoute un deuxième élément de projet de **récepteur d’événements** au projet, la même instance de votre extension est utilisée pour personnaliser le deuxième élément de projet.

 Pour accéder à une instance spécifique du type d’élément de projet que vous étendez, gérez l’un des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements du paramètre *projectItemType* dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode. Par exemple, pour déterminer quand un élément de projet du type que vous étendez est ajouté à un projet, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> événement. Pour plus d’informations, consultez [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identificateurs pour les éléments de projet SharePoint
 Chaque élément de projet SharePoint a un identificateur de chaîne correspondant. Vous devez connaître l’identificateur d’un élément de projet si vous souhaitez effectuer les tâches suivantes :

- Créez une extension pour l’élément de projet. Dans ce cas, vous devez passer l’identificateur de l’élément de projet que vous souhaitez étendre au constructeur de <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Pour créer une extension pour tous les types d’éléments de projet, transmettez la **\\** valeur * String.

- Ajoutez l’élément de projet à un projet par programmation. Dans ce cas, vous devez passer l’identificateur de l’élément de projet à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> méthode.

  Le tableau suivant répertorie les identificateurs pour les éléments de projet SharePoint inclus dans Visual Studio.

|Nom de l’élément de projet|Identificateur de chaîne|
|-----------------------|-----------------------|
|Modèle de Data Catalog d’entreprise|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Type de contenu|Microsoft. VisualStudio. SharePoint. ContentType|
|Récepteur d’événements|Microsoft. VisualStudio. SharePoint. EventHandler|
|Élément vide|Microsoft. VisualStudio. SharePoint. GenericElement|
|Définition de liste<br /><br /> Définition de liste à partir du type de contenu|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Instance de liste|Microsoft. VisualStudio. SharePoint. ListInstance|
|Module|Microsoft. VisualStudio. SharePoint. module|
|Flux de travail séquentiel<br /><br /> Flux de travail de l'ordinateur d'état|Microsoft. VisualStudio. SharePoint. Workflow|
|Définition de site|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Composant Visual Web part|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Composant Web Part|Microsoft. VisualStudio. SharePoint. WebPart|
|Formulaire d’association de flux de travail|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Voir aussi
- [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Comment : ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Comment : ajouter une propriété à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Procédure pas à pas : étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
