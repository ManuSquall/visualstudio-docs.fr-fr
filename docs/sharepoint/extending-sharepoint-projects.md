---
title: Extension des projets SharePoint | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 622596249e92d73dd4f504a445d43405847e9629
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="extending-sharepoint-projects"></a>Extension de projets SharePoint
  Créez une extension de projet lorsque vous souhaitez personnaliser des fonctionnalités au niveau du projet des projets SharePoint. Par exemple, vous pouvez ajouter des propriétés de projet personnalisées ou répondre à des événements au niveau du projet qui sont déclenchés lorsque l’utilisateur développe une solution SharePoint dans Visual Studio.  
  
## <a name="creating-project-extensions"></a>Création d’Extensions de projet  
 Pour étendre un élément de projet, créez un assembly d’extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Pour plus d’informations, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Lorsque vous créez une extension de projet, vous pouvez également ajouter les fonctionnalités suivantes pour les projets SharePoint :  
  
-   Ajouter un élément de menu contextuel. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel pour un nœud de projet SharePoint dans **l’Explorateur de solutions** en double-cliquant sur le nœud ou sélectionnant puis en choisissant le MAJ + F10 clés. Pour plus d’informations, consultez [Comment : ajouter un élément de Menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Ajouter une propriété personnalisée. La propriété apparaît dans le **propriétés** fenêtre lorsque vous choisissez un projet SharePoint dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Pour une procédure pas à pas qui montre comment créer, déployer et tester une extension de projet, consultez [procédure pas à pas : création d’une Extension de projet SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Présentation de la relation entre les Extensions et les Instances de projet  
 Lorsque vous créez une extension de projet, celle-ci est chargée lors de n’importe quel genre de projet SharePoint est ouvert dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] comprend plusieurs modèles de projet SharePoint, tels que les définitions de listes, les types de contenu et les récepteurs d’événements. Toutefois, il n'est qu’un seul type de projet SharePoint. Les types de projets qui s’affichent dans le **nouveau projet** boîte de dialogue sont uniquement des modèles qui regroupent un ou plusieurs éléments de projet SharePoint. Étant donné qu’un seul type de projet SharePoint, les extensions créées pour un projet s’appliquent à tous les projets SharePoint. Vous ne pouvez pas, par exemple, créer une extension qui s’applique uniquement à un **le Type de contenu** projet.  
  
 Pour accéder à une instance de projet spécifique, gérez l’un de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> les événements de la *projectService* paramètre dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> (méthode). Par exemple, pour déterminer quand un projet SharePoint est ajouté à une solution, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> événement. Pour plus d’informations, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Comment : ajouter un élément de Menu contextuel à des projets SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Procédure pas à pas : Création d’une Extension de projet SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Définition des Types d’éléments de projet SharePoint personnalisé](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Déploiement et l’extension empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  