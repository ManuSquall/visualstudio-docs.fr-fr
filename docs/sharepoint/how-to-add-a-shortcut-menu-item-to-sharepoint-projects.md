---
title: 'Comment : ajouter un élément de Menu contextuel à des projets SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 9a2fbc9d71684bc44e01a1d53f5d53f35c8d7311
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757570"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Comment : ajouter un élément de menu contextuel à des projets SharePoint
  Vous pouvez ajouter un élément de menu contextuel à un projet SharePoint. L’élément de menu s’affiche quand un utilisateur clique sur un nœud de projet dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d’informations, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Pour ajouter un élément de menu contextuel à des projets SharePoint  
  
1.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événements de la *projectService* paramètre.  
  
2.  Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événement, ajoutez une nouvelle <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> collection l’arguments du paramètre d’événement.  
  
3.  Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> Gestionnaire d’événements pour le nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches à exécuter lorsqu’un utilisateur clique sur votre élément de menu contextuel.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel aux nœuds de projet SharePoint de **l’Explorateur de solutions**. Lorsque l’utilisateur clique sur un nœud de projet et clique sur le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie** fenêtre. Cet exemple utilise le service de projet SharePoint pour afficher le message. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Déployer l’extension  
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi
 [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
