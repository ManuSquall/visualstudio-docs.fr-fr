---
title: Définition des types d’éléments de projet SharePoint personnalisés | Microsoft Docs
description: Définissez un type d’élément de projet SharePoint personnalisé lorsque vous souhaitez créer un nouveau genre d’élément de projet SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 00ee9f41695078d8bea5daacf1c0ccfd392a64cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948867"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Définir des types d’éléments de projet SharePoint personnalisés
  Définissez un nouveau type d’élément de projet SharePoint lorsque vous souhaitez créer un nouveau type d’élément de projet SharePoint. Par exemple, Visual Studio n’inclut pas les éléments de projet SharePoint pour l’ajout de champs ou d’actions personnalisées à un site SharePoint. Vous pouvez définir vos propres types d’éléments de projet SharePoint pour créer des champs, des actions personnalisées ou d’autres types de composants SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tâches pour la définition des types d’éléments de projet SharePoint
 Pour définir un type d’élément de projet personnalisé, générez un assembly d’extension Visual Studio qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface. Pour plus d’informations, consultez [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Lorsque vous définissez un type d’élément de projet personnalisé, vous pouvez également ajouter les fonctionnalités suivantes à l’élément de projet :

- Ajoutez un élément de menu contextuel à l’élément de projet. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel de l’élément de projet dans **Explorateur de solutions** en cliquant avec le bouton droit sur l’élément de projet ou en le sélectionnant, puis en choisissant les touches **MAJ** + **F10** . Pour plus d’informations, consultez [Comment : ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Ajoutez une propriété personnalisée à l’élément de projet. La propriété s’affiche dans la fenêtre **Propriétés** lorsque vous choisissez l’élément de projet dans **Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Pour permettre à d’autres développeurs d’utiliser votre élément de projet dans Visual Studio, créez un fichier. les données et créez un modèle d’élément ou un modèle de projet associé à l’élément de projet. Pour plus d’informations, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Comprendre la relation entre les types d’éléments de projet et les instances d’élément de projet
 Quand vous définissez un type d’élément de projet SharePoint, Visual Studio charge votre extension lorsqu’un élément de projet du type associé est ajouté à un projet SharePoint. Par exemple, si vous définissez un nouveau type d’élément de projet d' **action personnalisée** , Visual Studio charge votre extension quand un utilisateur ajoute un élément de projet d' **action personnalisée** à un projet. Visual Studio utilise la même instance de votre extension pour toutes les instances du type d’élément de projet associé. Dans l’exemple précédent, si l’utilisateur ajoute un deuxième élément de projet d' **action personnalisée** au projet, la même instance de votre extension est utilisée pour personnaliser le deuxième élément de projet.

 Pour accéder à une instance spécifique de votre type d’élément de projet, gérez l’un des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements du paramètre *projectItemTypeDefinition* dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode. Par exemple, pour déterminer quand un élément de projet de votre type personnalisé est ajouté à un projet, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> événement. Pour plus d’informations, consultez [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Voir aussi
- [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Comment : ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procédure pas à pas : créer un élément de projet d’action personnalisée avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
