---
title: "Comment : ajouter un élément de Menu contextuel à des projets SharePoint | Documents Microsoft"
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9427d2307a9d9726c2df1032410168c3b5cf1cc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Comment : ajouter un élément de menu contextuel à des projets SharePoint
  Vous pouvez ajouter un élément de menu contextuel à un projet SharePoint. L’élément de menu s’affiche lorsqu’un utilisateur clique sur un nœud de projet dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d’informations, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Pour ajouter un élément de menu contextuel à des projets SharePoint  
  
1.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> l’événement de la *projectService* paramètre.  
  
2.  Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événement, ajouter un nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> collection du paramètre d’arguments de l’événement.  
  
3.  Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> pour le nouveau gestionnaire d’événements <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches que vous souhaitez exécuter lorsqu’un utilisateur clique sur votre élément de menu contextuel.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel aux nœuds de projet SharePoint de **l’Explorateur de solutions**. Lorsque l’utilisateur clique un nœud de projet et clique sur le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie** fenêtre. Cet exemple utilise le service de projet SharePoint pour afficher le message. Pour plus d’informations, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Guide pratique pour ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  