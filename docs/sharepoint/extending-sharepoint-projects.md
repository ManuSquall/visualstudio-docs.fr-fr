---
title: Extension des projets SharePoint | Microsoft Docs
description: Découvrez comment créer une extension de projet lorsque vous souhaitez personnaliser les fonctionnalités au niveau du projet des projets SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ae4c3c1e606fd436725ef9f54a4568b754b048af
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672637"
---
# <a name="extend-sharepoint-projects"></a>Étendre des projets SharePoint
  Créez une extension de projet lorsque vous souhaitez personnaliser les fonctionnalités au niveau du projet des projets SharePoint. Par exemple, vous pouvez ajouter des propriétés de projet personnalisées ou répondre à des événements au niveau du projet qui sont déclenchés lorsque l’utilisateur développe une solution SharePoint dans Visual Studio.

## <a name="create-project-extensions"></a>Créer des extensions de projet
 Pour étendre un élément de projet, générez un assembly d’extension Visual Studio qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Pour plus d’informations, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Lorsque vous créez une extension de projet, vous pouvez également ajouter les fonctionnalités suivantes aux projets SharePoint :

- Ajoutez un élément de menu contextuel. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel d’un nœud de projet SharePoint dans **Explorateur de solutions** en cliquant avec le bouton droit sur le nœud ou en le sélectionnant, puis en choisissant les touches **MAJ** + **F10** . Pour plus d’informations, consultez [Comment : ajouter un élément de menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Ajoutez une propriété personnalisée. La propriété s’affiche dans la fenêtre **Propriétés** lorsque vous choisissez un projet SharePoint dans **Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Pour obtenir une procédure pas à pas qui montre comment créer, déployer et tester une extension de projet, consultez [procédure pas à pas : créer une extension de projet SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Comprendre la relation entre les extensions de projet et les instances de projet
 Lorsque vous créez une extension de projet, l’extension est chargée lorsque l’un des types de projet SharePoint est ouvert dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comprend plusieurs modèles de projet SharePoint, tels que les définitions de listes, les types de contenu et les récepteurs d’événements. Toutefois, il n’existe qu’un seul type de projet SharePoint. Les types de projets qui s’affichent dans la boîte de dialogue **nouveau projet** sont uniquement des modèles qui regroupent un ou plusieurs éléments de projet SharePoint. Étant donné qu’il n’existe qu’un seul type de projet SharePoint, les extensions créées pour un projet s’appliquent à tous les projets SharePoint. Par exemple, vous ne pouvez pas créer une extension qui s’applique uniquement à un projet de **type de contenu** .

 Pour accéder à une instance de projet spécifique, gérez l’un des <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> événements du paramètre *ProjectService* dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode. Par exemple, pour déterminer quand un projet SharePoint est ajouté à une solution, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> événement. Pour plus d’informations, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Comment : ajouter un élément de menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procédure pas à pas : créer une extension de projet SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
