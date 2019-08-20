---
title: Ajouter un élément de menu contextuel pour l’extension d’élément de projet SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8041f9cbf19d1e1324478b92d2655f1377102b81
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401638"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Procédure : Ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint
  Vous pouvez ajouter un élément de menu contextuel à un élément de projet SharePoint existant à l’aide d’une extension d’élément de projet. L’élément de menu s’affiche quand un utilisateur clique sur l’élément de projet dans **l’Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà créé une extension d’élément de projet. Pour plus d'informations, voir [Procédure : Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Pour ajouter un élément de menu contextuel dans une extension d’élément de projet

1. Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événements de la *projectItemType* paramètre.

2. Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événement, ajoutez une nouvelle <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> collection l’arguments du paramètre d’événement.

3. Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> Gestionnaire d’événements pour le nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches à exécuter lorsqu’un utilisateur clique sur votre élément de menu contextuel.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel à l’élément de projet de récepteur d’événements. Lorsque l’utilisateur clique sur l’élément de projet dans **l’Explorateur de solutions** et clique sur le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie**fenêtre.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 Cet exemple utilise le service de projet SharePoint pour écrire le message à la **sortie** fenêtre. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Guide pratique pour Ajouter une propriété à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procédure pas à pas : Étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
