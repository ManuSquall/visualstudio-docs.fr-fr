---
title: 'Procédure : Définir un Type d’élément de projet SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 589e6f5fd102cdd2a69bc63bf623142c14337678
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639230"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Procédure : Définir un type d’élément de projet SharePoint
  Définir un type d’élément de projet lorsque vous souhaitez créer un élément de projet SharePoint personnalisé. Pour plus d’informations, consultez [définition des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Pour définir un type d’élément de projet

1.  Créez un projet de bibliothèque de classes.

2.  Ajoutez des références aux assemblys suivants :

    -   Microsoft.VisualStudio.SharePoint

    -   System.ComponentModel.Composition

3.  Définissez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.

4.  Ajoutez les attributs suivants à la classe :

    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Cet attribut permet à Visual Studio détecter et charger votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation. Passer le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> type au constructeur d’attribut.

    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Dans une définition de type élément de projet, cet attribut spécifie l’identificateur de chaîne pour le nouvel élément de projet. Nous vous recommandons d’utiliser le format *nom de la société*. *nom de la fonctionnalité* pour s’assurer que tous les éléments de projet ont un nom unique.

    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Cet attribut spécifie l’icône à afficher pour cet élément de projet dans **l’Explorateur de solutions**. Cet attribut est facultatif ; Si vous n’appliquez pas à votre classe, Visual Studio affiche une icône par défaut pour votre élément de projet. Si vous définissez cet attribut, passez le nom qualifié complet d’une icône ou une bitmap qui est incorporée dans votre assembly.

5.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (méthode), utilisez les membres de la *projectItemTypeDefinition* paramètre pour définir le comportement du type d’élément de projet. Ce paramètre est un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objet qui fournit l’accès aux événements définis dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces. Pour accéder à une instance spécifique de votre type d’élément de projet, gérez <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> événements tels que <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment définir un type d’élément de projet simple. Ce type d’élément de projet écrit un message dans le **sortie** fenêtre et **liste d’erreurs** fenêtre lorsqu’un utilisateur ajoute un élément de projet de ce type à un projet.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 Cet exemple utilise le service de projet SharePoint pour écrire le message à la **sortie** fenêtre et **liste d’erreurs** fenêtre. Pour plus d’informations, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Déployer l’élément de projet
 Pour activer les autres développeurs d’utiliser votre élément de projet, créez un modèle de projet ou un modèle d’élément de projet. Pour plus d’informations, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Pour déployer l’élément de projet, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly, le modèle et tous les autres fichiers que vous souhaitez distribuer avec l’élément de projet. Pour plus d’informations, consultez [des outils de déploiement des Extensions pour SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Définir les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Créer des modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Guide pratique pour Ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Guide pratique pour Ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
