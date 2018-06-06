---
title: Associer des données personnalisées avec SharePoint les Extensions d’outils | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 051285d1a2b3fc1c32a813fbfd8aa778befa0545
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764873"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Associer des données personnalisées à des extensions d’outils SharePoint
  Vous pouvez ajouter des données personnalisées à certains objets dans les extensions d’outils SharePoint. Cela est utile lorsque vous disposez de données dans une partie de votre extension que vous souhaitez accéder ultérieurement à partir de tout autre code dans votre extension. Au lieu d’implémenter une manière personnalisée pour stocker et accéder aux données, vous pouvez associer les données à un objet dans votre extension et récupérer les données à partir du même objet ultérieurement.  
  
 Ajouter des données personnalisées aux objets est également utile lorsque vous souhaitez conserver les données qui s’applique à un élément spécifique dans Visual Studio. Les extensions d’outils SharePoint sont chargées qu’une fois dans Visual Studio, par conséquent, votre extension peut fonctionner avec plusieurs éléments différents (tels que les projets, des éléments de projet ou **l’Explorateur de serveurs** nœuds) à tout moment. Si vous avez des données personnalisées qui s’applique uniquement à un élément spécifique, vous pouvez ajouter les données à l’objet qui représente cet élément.  
  
 Lorsque vous ajoutez des données personnalisées aux objets dans les extensions d’outils SharePoint, les données ne sont pas conservent. Les données sont disponibles uniquement pendant la durée de vie de l’objet. Une fois que l’objet soit récupéré par le garbage collection, les données sont perdues.  
  
 Dans les extensions du système de projet SharePoint, vous pouvez également enregistrer des données de chaîne qui persiste après qu’une extension est déchargée. Pour plus d’informations, consultez [l’enregistrement des données dans les Extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Objets qui peuvent contenir des données
 Vous pouvez ajouter des données personnalisées à n’importe quel objet dans le modèle objet des outils SharePoint qui implémente le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Cette interface définit qu’une seule propriété, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, qui est une collection d’objets de données personnalisés. Les types suivants implémentent <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>Ajouter et récupérer des données personnalisées
 Pour ajouter des données personnalisées à un objet dans une extension des outils SharePoint, obtenez la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’objet que vous souhaitez ajouter les données, puis utiliser le <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> méthode pour ajouter les données à l’objet.  
  
 Pour récupérer des données personnalisées à partir d’un objet dans une extension des outils SharePoint, obtenez le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’objet et puis utilisez une des méthodes suivantes :  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Cette méthode retourne **true** si l’objet de données existe, ou **false** s’il n’existe pas. Vous pouvez utiliser cette méthode pour récupérer des instances de types valeur ou des types référence.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Cette méthode retourne les données d’objet si elle se termine, ou **null** s’il n’existe pas. Vous pouvez utiliser cette méthode uniquement pour récupérer des instances de types de référence.  
  
 L’exemple de code suivant détermine si un objet de données est déjà associé à un élément de projet. Si l’objet de données n’est pas déjà associé à l’élément de projet, puis le code ajoute l’objet à le <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l’élément de projet. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : ajouter une propriété à un Type d’élément de projet personnalisé SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Voir aussi
 [Concepts de programmation et les fonctionnalités des Extensions des outils SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procédure pas à pas : Extension de l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Guide pratique pour ajouter une propriété à un type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
   
 