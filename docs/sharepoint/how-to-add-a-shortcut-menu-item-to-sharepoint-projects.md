---
title: 'Comment : ajouter un élément de menu contextuel à des projets SharePoint | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: ea862eb21aaee75499f3b1bac7007063227150e2
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585847"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Comment : ajouter un élément de menu contextuel à des projets SharePoint
  Vous pouvez ajouter un élément de menu contextuel à n’importe quel projet SharePoint. L’élément de menu s’affiche lorsqu’un utilisateur clique avec le bouton droit sur un nœud de projet dans **Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà créé une extension de projet. Pour plus d’informations, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Pour ajouter un élément de menu contextuel à des projets SharePoint

1. Dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événement du paramètre *ProjectService* .

2. Dans votre gestionnaire d’événements pour l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> événement, ajoutez un nouvel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objet à <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> collection ou du paramètre d’arguments d’événement.

3. Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> Gestionnaire d’événements du nouvel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objet, effectuez les tâches que vous souhaitez exécuter lorsqu’un utilisateur clique sur l’élément de menu contextuel.

## <a name="example"></a> Exemple
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel à des nœuds de projet SharePoint dans **Explorateur de solutions**. Quand l’utilisateur clique avec le bouton droit sur un nœud de projet et clique sur l’élément **de menu écrire un message dans fenêtre Sortie** , Visual Studio affiche un message dans la fenêtre **sortie** . Cet exemple utilise le service de projet SharePoint pour afficher le message. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
