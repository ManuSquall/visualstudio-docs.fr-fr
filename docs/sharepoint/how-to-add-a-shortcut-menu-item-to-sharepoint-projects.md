---
title: 'Procédure : Ajouter un élément de Menu contextuel à des projets SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 5b5db3fe3aaf8dc57c7df6a63810106ae9fb30fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115586"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Procédure : Ajouter un élément de menu contextuel à des projets SharePoint
  Vous pouvez ajouter un élément de menu contextuel à un projet SharePoint. L’élément de menu s’affiche quand un utilisateur clique sur un nœud de projet dans **l’Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d'informations, voir [Procédure : Créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Pour ajouter un élément de menu contextuel à des projets SharePoint

1. Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événements de la *projectService* paramètre.

2. Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événement, ajoutez une nouvelle <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> collection l’arguments du paramètre d’événement.

3. Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> Gestionnaire d’événements pour le nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches à exécuter lorsqu’un utilisateur clique sur votre élément de menu contextuel.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel aux nœuds de projet SharePoint de **l’Explorateur de solutions**. Lorsque l’utilisateur clique sur un nœud de projet et clique sur le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie** fenêtre. Cet exemple utilise le service de projet SharePoint pour afficher le message. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Guide pratique pour Créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Guide pratique pour Ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
