---
title: 'Procédure : Ajouter un élément de Menu contextuel à un Type d’élément de projet SharePoint personnalisé | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7de1bf04137c0e799e19e658307d630ec3fa6a78
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068741"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Procédure : Ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé
  Lorsque vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez ajouter un élément de menu contextuel pour l’élément de projet. L’élément de menu s’affiche quand un utilisateur clique sur l’élément de projet dans **l’Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà défini votre propre type d’élément de projet SharePoint. Pour plus d'informations, voir [Procédure : Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Pour ajouter un élément de menu contextuel à un type d’élément de projet personnalisé

1. Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événements de la *projectItemTypeDefinition* paramètre.

2. Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événement, ajoutez une nouvelle <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> collection l’arguments du paramètre d’événement.

3. Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> Gestionnaire d’événements pour le nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches à exécuter lorsqu’un utilisateur choisit de votre élément de menu contextuel.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel à un type d’élément de projet personnalisé. Lorsque l’utilisateur ouvre le menu contextuel à partir de l’élément de projet dans **l’Explorateur de solutions** et choisit le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie**  fenêtre.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 Cet exemple utilise le service de projet SharePoint pour écrire le message à la **sortie** fenêtre. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Déployer l’élément de projet
 Pour activer les autres développeurs d’utiliser votre élément de projet, créez un modèle de projet ou un modèle d’élément de projet. Pour plus d’informations, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Pour déployer l’élément de projet, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly, le modèle et tous les autres fichiers que vous souhaitez distribuer avec l’élément de projet. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Guide pratique pour Ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Définition des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
