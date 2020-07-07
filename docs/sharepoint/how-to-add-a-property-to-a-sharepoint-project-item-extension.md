---
title: 'Comment : ajouter une propriété à une extension d’élément de projet SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 337536d2219ce8494f96769bc79f10967883e61a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015982"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Comment : ajouter une propriété à une extension d’élément de projet SharePoint
  Vous pouvez utiliser une extension d’élément de projet pour ajouter une propriété à un élément de projet SharePoint déjà installé dans Visual Studio. La propriété s’affiche dans la fenêtre **Propriétés** lorsque l’élément de projet est sélectionné dans **Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà créé une extension d’élément de projet. Pour plus d’informations, consultez [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Pour ajouter une propriété à une extension d’élément de projet

1. Définissez une classe avec une propriété publique qui représente la propriété que vous ajoutez à un type d’élément de projet. Si vous souhaitez ajouter plusieurs propriétés à un type d’élément de projet, vous pouvez définir toutes les propriétés dans la même classe ou dans des classes différentes.

2. Dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement du paramètre *projectItemType* .

3. Dans le gestionnaire d’événements pour l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> collection du paramètre d’arguments d’événement.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter une propriété nommée **example Property** à l’élément de projet récepteur d’événements.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Comprendre le code
 Pour vous assurer que la même instance de la `CustomProperties` classe est utilisée chaque fois que l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement se produit, l’exemple de code ajoute l’objet de propriétés à la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’élément de projet la première fois que cet événement se produit. Le code récupère cet objet chaque fois que cet événement se reproduit. Pour plus d’informations sur l’utilisation <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de la propriété pour associer des données à des éléments de projet, consultez [associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Pour conserver les modifications apportées à la valeur de la propriété, l’accesseur **Set** pour `ExampleProperty` enregistre la nouvelle valeur dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété de l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet auquel la propriété est associée. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour rendre des données persistantes avec des éléments de projet, consultez [enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte dans la fenêtre **Propriétés** en appliquant des attributs de l' <xref:System.ComponentModel> espace de noms à la définition de propriété. Les attributs suivants sont utiles dans de nombreux scénarios :

- <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans la fenêtre **Propriétés** .

- <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît en bas de la fenêtre **Propriétés** lorsque la propriété est sélectionnée.

- <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.

- <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne affichée dans la fenêtre **Propriétés** et une valeur de propriété qui n’est pas une chaîne.

- <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.

## <a name="compile-the-code"></a>Compiler le code
 Ces exemples requièrent un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Comment : ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procédure pas à pas : étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
