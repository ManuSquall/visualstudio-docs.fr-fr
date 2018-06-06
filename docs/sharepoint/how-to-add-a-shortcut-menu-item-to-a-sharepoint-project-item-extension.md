---
title: 'Comment : ajouter un élément de Menu contextuel à une Extension d’élément de projet SharePoint | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98b85396f2d659fa46a8918d670cc5e9558cf2ca
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766761"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Comment : ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint
  Vous pouvez ajouter un élément de menu contextuel à un élément de projet SharePoint existant à l’aide d’une extension d’élément de projet. L’élément de menu s’affiche lorsqu’un utilisateur clique sur l’élément de projet dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà créé une extension d’élément de projet. Pour plus d’informations, consultez [Comment : créer une Extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Pour ajouter un élément de menu contextuel dans une extension d’élément de projet  
  
1.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> l’événement de la *projectItemType* paramètre.  
  
2.  Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événement, ajouter un nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> collection du paramètre d’arguments de l’événement.  
  
3.  Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> pour le nouveau gestionnaire d’événements <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches que vous souhaitez exécuter lorsqu’un utilisateur clique sur votre élément de menu contextuel.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel pour l’élément de projet récepteur d’événements. Lorsque l’utilisateur clique sur l’élément de projet dans **l’Explorateur de solutions** et clique sur le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie**fenêtre.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message à la **sortie** fenêtre. Pour plus d’informations, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi
 [Comment : créer une Extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Comment : ajouter une propriété à une Extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procédure pas à pas : extension d’un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
