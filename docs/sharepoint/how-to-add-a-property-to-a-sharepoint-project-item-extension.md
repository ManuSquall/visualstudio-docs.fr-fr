---
title: 'Procédure : Ajouter une propriété à une Extension d’élément de projet SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 6dc2c0588fa3078a805f9804263afcf521ae72ed
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644427"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Procédure : Ajouter une propriété à une extension d’élément de projet SharePoint
  Vous pouvez utiliser une extension d’élément de projet pour ajouter une propriété à n’importe quel élément de projet SharePoint qui est déjà installé dans Visual Studio. La propriété apparaît dans le **propriétés** fenêtre lorsque l’élément de projet est sélectionné dans **l’Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà créé une extension d’élément de projet. Pour plus d'informations, voir [Procédure : Créer une Extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Pour ajouter une propriété à une extension d’élément de projet

1.  Définir une classe avec une propriété publique qui représente la propriété que vous ajoutez à un type d’élément de projet. Si vous souhaitez ajouter plusieurs propriétés à un type d’élément de projet, vous pouvez définir toutes les propriétés dans la même classe ou dans différentes classes.

2.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événements de la *projectItemType* paramètre.

3.  Dans le Gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés pour le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> collection l’arguments du paramètre d’événement.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter une propriété nommée **exemple de propriété** à l’élément de projet de récepteur d’événements.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Comprendre le code
 Pour vous assurer que la même instance de la `CustomProperties` classe est utilisée chaque fois que le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement se produit, l’exemple de code ajoute l’objet de propriétés pour le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’élément la première de projet fois cet événement se produit. Le code récupère cet objet chaque fois que cet événement se produit à nouveau. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété à associer des données à des éléments de projet, consultez [associer des données personnalisées à SharePoint extensions d’outils](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Pour conserver les modifications apportées à la valeur de propriété, le **définir** accesseur pour `ExampleProperty` enregistre la nouvelle valeur à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet auquel la propriété est associée. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour conserver les données avec des éléments de projet, consultez [enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte de la **propriétés** fenêtre en appliquant des attributs à partir de la <xref:System.ComponentModel> la définition de propriété de l’espace de noms. Les attributs suivants sont utiles dans de nombreux scénarios :

-   <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans le **propriétés** fenêtre.

-   <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît en bas de la **propriétés** fenêtre lorsque la propriété est sélectionnée.

-   <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.

-   <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne qui est affichée dans le **propriétés** fenêtre et une valeur de propriété de non-chaîne.

-   <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.

## <a name="compile-the-code"></a>Compiler le code
 Ces exemples nécessitent un projet de bibliothèque de classes avec des références aux assemblys suivants :

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Guide pratique pour Ajouter un élément de menu contextuel à une extension d’élément de projet SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procédure pas à pas : Étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
