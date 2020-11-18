---
title: Ajouter un élément de menu contextuel au type d’élément de projet SharePoint personnalisé
titleSuffix: ''
description: Savoir comment ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé. L’élément de menu s’affiche lorsque vous cliquez avec le bouton droit sur l’élément de projet dans Explorateur de solutions.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2916b806c6e149a9c0cbe2495a7edabcfc883e7e
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850076"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Comment : ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé
  Lorsque vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez ajouter un élément de menu contextuel à l’élément de projet. L’élément de menu s’affiche lorsqu’un utilisateur clique avec le bouton droit sur l’élément de projet dans **Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà défini votre propre type d’élément de projet SharePoint. Pour plus d’informations, consultez [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Pour ajouter un élément de menu contextuel à un type d’élément de projet personnalisé

1. Dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événement du paramètre *projectItemTypeDefinition* .

2. Dans votre gestionnaire d’événements pour l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événement, ajoutez un nouvel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objet à <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> collection ou du paramètre d’arguments d’événement.

3. Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> Gestionnaire d’événements du nouvel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objet, effectuez les tâches que vous souhaitez exécuter lorsqu’un utilisateur choisit l’élément de menu contextuel.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel à un type d’élément de projet personnalisé. Lorsque l’utilisateur ouvre le menu contextuel à partir de l’élément de projet dans **Explorateur de solutions** et choisit l’élément de menu **écrire le message dans fenêtre Sortie** , Visual Studio affiche un message dans la fenêtre **sortie** .

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 Cet exemple utilise le service de projet SharePoint pour écrire le message dans la fenêtre **sortie** . Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Déployer l’élément de projet
 Pour permettre à d’autres développeurs d’utiliser votre élément de projet, créez un modèle de projet ou un modèle d’élément de projet. Pour plus d’informations, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Pour déployer l’élément de projet, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly, le modèle et tous les autres fichiers que vous souhaitez distribuer avec l’élément de projet. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Définition des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
