---
title: Association de données personnalisées à des extensions d’outils SharePoint | Microsoft Docs
description: Associer des données personnalisées à des extensions d’outils SharePoint. Consultez la liste des objets pouvant contenir des données personnalisées. Ajoutez et récupérez des données personnalisées.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5665fc28bacb76c6887cb7dcb1820ec9dc0d2b3a
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215316"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Associer des données personnalisées à des extensions d’outils SharePoint
  Vous pouvez ajouter des données personnalisées à certains objets dans les extensions des outils SharePoint. Cela est utile lorsque vous disposez de données dans une partie de votre extension auxquelles vous souhaitez accéder ultérieurement à partir d’un autre code dans votre extension. Au lieu d’implémenter une méthode personnalisée pour stocker des données et y accéder, vous pouvez associer les données à un objet dans votre extension, puis récupérer ultérieurement les données du même objet.

 L’ajout de données personnalisées aux objets est également utile lorsque vous souhaitez conserver les données pertinentes pour un élément spécifique dans Visual Studio. Les extensions des outils SharePoint sont chargées une seule fois dans Visual Studio. par conséquent, votre extension peut fonctionner avec plusieurs éléments différents (tels que des projets, des éléments de projet ou des nœuds de **Explorateur de serveurs** ) à tout moment. Si vous avez des données personnalisées qui s’appliquent uniquement à un élément spécifique, vous pouvez ajouter les données à l’objet qui représente cet élément.

 Lorsque vous ajoutez des données personnalisées à des objets dans les extensions des outils SharePoint, les données ne sont pas conservées. Les données sont disponibles uniquement pendant la durée de vie de l’objet. Une fois l’objet récupéré par garbage collection, les données sont perdues.

 Dans les extensions du système de projet SharePoint, vous pouvez également enregistrer des données de chaîne qui persistent après le déchargement d’une extension. Pour plus d’informations, consultez [enregistrement des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Objets pouvant contenir des données personnalisées
 Vous pouvez ajouter des données personnalisées à n’importe quel objet dans le modèle objet des outils SharePoint qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Cette interface définit une seule propriété, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> , qui est une collection d’objets de données personnalisés. Les types suivants implémentent <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Ajouter et récupérer des données personnalisées
 Pour ajouter des données personnalisées à un objet dans une extension d’outils SharePoint, récupérez la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’objet auquel vous souhaitez ajouter les données, puis utilisez la <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> méthode pour ajouter les données à l’objet.

 Pour récupérer des données personnalisées à partir d’un objet dans une extension d’outils SharePoint, récupérez la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’objet, puis utilisez l’une des méthodes suivantes :

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Cette méthode retourne la **valeur true** si l’objet de données existe, ou **false** s’il n’existe pas. Vous pouvez utiliser cette méthode pour récupérer des instances de types valeur ou de types référence.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Cette méthode retourne l’objet de données s’il se termine, ou **null** s’il n’existe pas. Vous pouvez utiliser cette méthode uniquement pour récupérer des instances de types référence.

  L’exemple de code suivant détermine si un objet de données est déjà associé à un élément de projet. Si l’objet de données n’est pas déjà associé à l’élément de projet, le code ajoute l’objet à la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’élément de projet. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet13":::
  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet13":::

## <a name="see-also"></a>Voir aussi
- [Concepts et fonctionnalités de programmation pour les extensions des outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procédure pas à pas : extension de Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Comment : ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
