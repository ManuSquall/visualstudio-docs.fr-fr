---
title: "Définition des Types d’éléments de projet SharePoint personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e627d78e5c040614c29e7503cd7efab728b02bfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="defining-custom-sharepoint-project-item-types"></a>Définition de types d'éléments de projet SharePoint personnalisés
  Définir un nouveau type d’élément de projet SharePoint lorsque vous souhaitez créer un nouveau type d’élément de projet SharePoint. Par exemple, Visual Studio n’inclut pas les éléments de projet SharePoint pour l’ajout de champs ou des actions personnalisées à un site SharePoint. Vous pouvez définir vos propres types d’éléments de projet SharePoint pour la création de champs, des actions personnalisées ou autres types de composants SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tâches pour définir des Types d’éléments de projet SharePoint  
 Pour définir un type d’élément de projet personnalisé, générez un assembly d’extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface. Pour plus d’informations, consultez [Comment : définir un Type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Lorsque vous définissez un type d’élément de projet personnalisé, vous pouvez également ajouter les fonctionnalités suivantes à l’élément de projet :  
  
-   Ajouter un élément de menu contextuel pour l’élément de projet. L’élément de menu s’affiche lorsque vous ouvrez le menu contextuel pour l’élément de projet dans **l’Explorateur de solutions** des clés en double-cliquant sur l’élément de projet ou en le sélectionnant et en appuyant sur la touche MAJ + F10. Pour plus d’informations, consultez [Comment : ajouter un élément de Menu contextuel à un Type d’élément de projet personnalisé SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Ajouter une propriété personnalisée à l’élément de projet. La propriété apparaît dans le **propriétés** fenêtre lorsque vous choisissez l’élément de projet dans **l’Explorateur de solutions**. Pour plus d’informations, consultez [Comment : ajouter une propriété à un Type d’élément de projet personnalisé SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Pour activer les autres développeurs d’utiliser votre élément de projet dans Visual Studio, créez un fichier .spdata et créer un modèle d’élément ou d’un modèle de projet qui est associé à l’élément de projet. Pour plus d’informations, consultez [création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understanding-the-relationship-between-project-item-types-and-project-item-instances"></a>Présentation de la relation entre les Types d’éléments de projet et les Instances d’élément de projet  
 Lorsque vous définissez un type d’élément de projet SharePoint, Visual Studio charge votre extension lorsqu’un élément de projet du type associé est ajouté à un projet SharePoint. Par exemple, si vous définissez un nouveau **Action personnalisée** type d’élément de projet, Visual Studio charge votre extension lorsqu’un utilisateur ajoute un **Action personnalisée** élément de projet pour un projet. Visual Studio utilise la même instance de votre extension pour toutes les instances du type d’élément de projet associé. Dans l’exemple précédent, si l’utilisateur ajoute un deuxième **Action personnalisée** d’éléments de projet au projet, la même instance de votre extension est utilisée pour personnaliser le deuxième élément de projet.  
  
 Pour accéder à une instance spécifique de votre type d’élément de projet, gérez l’un de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> les événements de la *projectItemTypeDefinition* paramètre dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (méthode). Par exemple, pour déterminer quand un élément de projet de votre type personnalisé est ajouté à un projet, gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> événement. Pour plus d’informations, consultez [Comment : définir un Type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir un Type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Comment : ajouter une propriété à un Type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Comment : ajouter un élément de Menu contextuel à un Type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procédure pas à pas : Création d’un élément de projet de colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Procédure pas à pas : Création d’un élément de projet de colonne de Site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Déploiement d’extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  