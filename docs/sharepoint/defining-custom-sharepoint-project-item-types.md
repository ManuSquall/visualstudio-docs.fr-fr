---
title: Définition des Types d’éléments de projet SharePoint personnalisé | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5f32abba4c4cbdeab59ed66e38019d913e704e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580782"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Définir les types d’éléments de projet SharePoint personnalisés
  Définir un nouveau type d’élément de projet SharePoint lorsque vous souhaitez créer un nouveau genre d’élément de projet SharePoint. Par exemple, Visual Studio n’inclut pas les éléments de projet SharePoint pour l’ajout de champs ou des actions personnalisées sur un site SharePoint. Vous pouvez définir vos propres types d’éléments de projet SharePoint pour la création de champs, d’actions personnalisées ou d’autres types de composants SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tâches pour la définition des types d’éléments de projet SharePoint
 Pour définir un type d’élément de projet personnalisé, générez un assembly d’extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface. Pour plus d'informations, voir [Procédure : Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Lorsque vous définissez un type d’élément de projet personnalisé, vous pouvez également ajouter les fonctionnalités suivantes à l’élément de projet :

- Ajouter un élément de menu contextuel à l’élément de projet. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel de l’élément de projet dans **l’Explorateur de solutions** en double-cliquant sur l’élément de projet ou en sélectionnant puis en choisissant le **MAJ** +  **F10** clés. Pour plus d'informations, voir [Procédure : Ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Ajouter une propriété personnalisée à l’élément de projet. La propriété apparaît dans le **propriétés** fenêtre lorsque vous choisissez l’élément de projet dans **l’Explorateur de solutions**. Pour plus d'informations, voir [Procédure : Ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Pour activer les autres développeurs d’utiliser votre élément de projet dans Visual Studio, créez un fichier .spdata et créer un modèle d’élément ou d’un modèle de projet qui est associé à l’élément de projet. Pour plus d’informations, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Comprendre la relation entre les types d’éléments de projet et les instances d’élément de projet
 Lorsque vous définissez un type d’élément de projet SharePoint, Visual Studio charge votre extension lors de l’ajout d’un élément de projet du type associé à un projet SharePoint. Par exemple, si vous définissez une nouvelle **Custom Action** type d’élément de projet, Visual Studio charge votre extension lorsqu’un utilisateur ajoute un **Custom Action** élément de projet à un projet. Visual Studio utilise la même instance de votre extension pour toutes les instances du type d’élément de projet associé. Dans l’exemple précédent, si l’utilisateur ajoute un deuxième **Custom Action** l’élément de projet au projet, la même instance de votre extension est utilisée pour personnaliser le deuxième élément de projet.

 Pour accéder à une instance spécifique de votre type d’élément de projet, gérez l’un de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements de la *projectItemTypeDefinition* paramètre dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (méthode). Par exemple, pour déterminer quand un élément de projet de votre type personnalisé est ajouté à un projet, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> événement. Pour plus d'informations, voir [Procédure : Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Guide pratique pour Ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Guide pratique pour Ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Créer des modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procédure pas à pas : Créer un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
