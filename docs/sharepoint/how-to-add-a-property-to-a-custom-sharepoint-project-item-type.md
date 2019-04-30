---
title: 'Procédure : Ajouter une propriété à un Type d’élément de projet SharePoint personnalisé | Microsoft Docs'
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
ms.openlocfilehash: e9695755967aa1b66aa7cda2d784ae88b0fc1b42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967290"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Procédure : Ajouter une propriété à un type d’élément de projet SharePoint personnalisé
  Lorsque vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez ajouter une propriété à l’élément de projet. La propriété apparaît dans le **propriétés** fenêtre lorsque l’élément de projet est sélectionné dans **l’Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà défini votre propre type d’élément de projet SharePoint. Pour plus d'informations, voir [Procédure : Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Pour ajouter une propriété à une définition d’un type d’élément de projet

1. Définir une classe avec une propriété publique qui représente la propriété que vous ajoutez au type d’élément de projet personnalisé. Si vous souhaitez ajouter plusieurs propriétés à un type d’élément de projet personnalisé, vous pouvez définir toutes les propriétés dans la même classe ou dans différentes classes.

2. Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événements de la *projectItemTypeDefinition* paramètre.

3. Dans le Gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés personnalisées pour le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> collection l’arguments du paramètre d’événement.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter une propriété nommée **exemple de propriété** personnalisée élément type de projet.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Comprendre le code
 Pour vous assurer que la même instance de la `CustomProperties` classe est utilisée chaque fois que le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement se produit, l’exemple de code enregistre l’objet de propriétés dans le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’élément la première de projet fois cet événement se produit. Le code récupère cet objet chaque fois que cet événement se produit à nouveau. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété pour enregistrer les données avec des éléments de projet, consultez [associer des données personnalisées à SharePoint extensions d’outils](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Pour conserver les modifications apportées à la valeur de propriété, le **définir** accesseur pour `ExampleProperty` enregistre la nouvelle valeur à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet auquel la propriété est associée. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour conserver les données avec des éléments de projet, consultez [enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte de la **propriétés** fenêtre en appliquant des attributs à partir de la <xref:System.ComponentModel> la définition de propriété de l’espace de noms. Les attributs suivants sont utiles dans de nombreux scénarios :

- <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans le **propriétés** fenêtre.

- <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît en bas de la **propriétés** fenêtre lorsque la propriété est sélectionnée.

- <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.

- <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne qui est affichée dans le **propriétés** fenêtre et une valeur de propriété de non-chaîne.

- <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.

## <a name="compile-the-code"></a>Compiler le code
 Ces exemples de code nécessitent un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Déployer l’élément de projet
 Pour activer les autres développeurs d’utiliser votre élément de projet, créez un modèle de projet ou un modèle d’élément de projet. Pour plus d’informations, consultez [créer des modèles de projet pour les éléments de projet SharePoint et de modèles d’élément](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Pour déployer l’élément de projet, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly, le modèle et tous les autres fichiers que vous souhaitez distribuer avec l’élément de projet. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Guide pratique pour Ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Définition des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
