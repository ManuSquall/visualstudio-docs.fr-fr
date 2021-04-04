---
title: Ajouter une propriété au type d’élément de projet SharePoint personnalisé
description: Ajoutez une propriété à un type d’élément de projet SharePoint personnalisé. La propriété apparaît dans la Fenêtre Propriétés lorsque l’élément de projet est sélectionné dans Explorateur de solutions.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17d9ac144b97c090292395dd5ae5e85319dd1308
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215511"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé
  Quand vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez ajouter une propriété à l’élément de projet. La propriété s’affiche dans la fenêtre **Propriétés** lorsque l’élément de projet est sélectionné dans **Explorateur de solutions**.

 Les étapes suivantes supposent que vous avez déjà défini votre propre type d’élément de projet SharePoint. Pour plus d’informations, consultez [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Pour ajouter une propriété à une définition d’un type d’élément de projet

1. Définissez une classe avec une propriété publique qui représente la propriété que vous ajoutez au type d’élément de projet personnalisé. Si vous souhaitez ajouter plusieurs propriétés à un type d’élément de projet personnalisé, vous pouvez définir toutes les propriétés dans la même classe ou dans des classes différentes.

2. Dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement du paramètre *projectItemTypeDefinition* .

3. Dans le gestionnaire d’événements pour l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement, ajoutez une instance de votre classe de propriétés personnalisées à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> collection du paramètre d’arguments d’événement.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment ajouter une propriété nommée **example Property** à un type d’élément de projet personnalisé.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet11":::

### <a name="understand-the-code"></a>Comprendre le code
 Pour vous assurer que la même instance de la `CustomProperties` classe est utilisée chaque fois que l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> événement se produit, l’exemple de code enregistre l’objet de propriétés dans la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’élément de projet la première fois que cet événement se produit. Le code récupère cet objet chaque fois que cet événement se reproduit. Pour plus d’informations sur l’utilisation <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de la propriété pour enregistrer des données avec des éléments de projet, consultez [associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Pour conserver les modifications apportées à la valeur de la propriété, l’accesseur **Set** pour `ExampleProperty` enregistre la nouvelle valeur dans la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété de l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objet auquel la propriété est associée. Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriété pour rendre des données persistantes avec des éléments de projet, consultez [enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Spécifier le comportement des propriétés personnalisées
 Vous pouvez définir la façon dont une propriété personnalisée apparaît et se comporte dans la fenêtre **Propriétés** en appliquant des attributs de l' <xref:System.ComponentModel> espace de noms à la définition de propriété. Les attributs suivants sont utiles dans de nombreux scénarios :

- <xref:System.ComponentModel.DisplayNameAttribute>: Spécifie le nom de la propriété qui s’affiche dans la fenêtre **Propriétés** .

- <xref:System.ComponentModel.DescriptionAttribute>: Spécifie la chaîne de description qui apparaît en bas de la fenêtre **Propriétés** lorsque la propriété est sélectionnée.

- <xref:System.ComponentModel.DefaultValueAttribute>: Spécifie la valeur par défaut de la propriété.

- <xref:System.ComponentModel.TypeConverterAttribute>: Spécifie une conversion personnalisée entre la chaîne affichée dans la fenêtre **Propriétés** et une valeur de propriété qui n’est pas une chaîne.

- <xref:System.ComponentModel.EditorAttribute>: Spécifie un éditeur personnalisé à utiliser pour modifier la propriété.

## <a name="compile-the-code"></a>Compiler le code
 Ces exemples de code requièrent un projet de bibliothèque de classes avec des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Déployer l’élément de projet
 Pour permettre à d’autres développeurs d’utiliser votre élément de projet, créez un modèle de projet ou un modèle d’élément de projet. Pour plus d’informations, consultez [créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Pour déployer l’élément de projet, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly, le modèle et tous les autres fichiers que vous souhaitez distribuer avec l’élément de projet. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Comment : ajouter un élément de menu contextuel à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Définition des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
