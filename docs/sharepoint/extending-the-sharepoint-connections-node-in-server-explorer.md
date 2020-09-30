---
title: Extension du nœud Connexions SharePoint dans Explorateur de serveurs | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6615e02d84e1f252800597cb37666557e3c3fee6
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584605"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Étendre le nœud Connexions SharePoint dans Explorateur de serveurs
  Dans Visual Studio, vous pouvez vous connecter à des sites SharePoint locaux sur l’ordinateur de développement à l’aide du nœud **Connexions SharePoint** dans la fenêtre **Explorateur de serveurs** . Ce nœud affiche un grand nombre des composants des sites SharePoint locaux dans une arborescence hiérarchique. Par exemple, vous pouvez afficher les listes, les bibliothèques de documents et les types de contenu sur les sites locaux. Pour plus d’informations sur l’utilisation de **Explorateur de serveurs** pour se connecter à des sites SharePoint locaux, consultez [Parcourir les connexions SharePoint à l’aide de Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Vous pouvez étendre le nœud **Connexions SharePoint** en créant des extensions pour les nœuds existants, ou en créant un type de nœud personnalisé et en l’ajoutant à la hiérarchie des nœuds.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Tâches d’extension du nœud Connexions SharePoint
 Pour étendre un nœud existant, créez une extension Visual Studio qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Lorsque vous étendez un nœud, vous pouvez ajouter des fonctionnalités au nœud, telles que vos propres éléments de menu contextuel ou propriétés personnalisées. Pour plus d’informations, consultez [Comment : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Pour créer un type de nœud personnalisé, créez une extension Visual Studio qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Créez un nœud personnalisé si vous souhaitez afficher les composants des sites SharePoint qui ne sont pas affichés dans **Explorateur de serveurs** par défaut. Par exemple, **Explorateur de serveurs** n’affiche pas la Galerie de composants WebPart d’un site SharePoint par défaut, mais vous pouvez ajouter un nœud personnalisé qui fait cela. Pour plus d’informations, consultez [procédure : ajouter un nœud SharePoint personnalisé à Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) et [procédure pas à pas : étendre des Explorateur de serveurs pour afficher composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Ajouter des propriétés personnalisées aux nœuds
 Lorsque vous étendez un nœud ou créez un type de nœud personnalisé, vous pouvez ajouter des propriétés personnalisées au nœud. Les propriétés s’affichent dans le **propriétés** fenêtre lorsque le nœud est sélectionné.

 Il existe deux types de propriétés personnalisées que vous pouvez ajouter à un nœud :

- Propriétés qui affichent un jeu de données en lecture seule à partir du site SharePoint. Les données décrivent le composant SharePoint représenté par le nœud. Pour obtenir une procédure pas à pas qui montre comment procéder, consultez [procédure pas à pas : étendre Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Propriétés qui affichent des données en lecture/écriture personnalisées. Pour obtenir un exemple de code qui montre comment procéder, consultez [Comment : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Obtenir des données pour les nœuds intégrés
 Tous les nœuds intégrés fournis par Visual Studio incluent des données sur le composant SharePoint qu’ils représentent. Par exemple, un nœud qui représente une liste sur le site SharePoint fournit des données relatives à la liste, telles que le titre et l’URL de la vue par défaut de la liste.

 Pour accéder à ces données, récupérez un objet de données de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet qui représente le nœud qui vous intéresse. Le type de l’objet de données dépend du type du nœud.

 L’exemple de code suivant montre comment obtenir l’objet de données pour un nœud de liste. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : obtenir des données pour un nœud SharePoint intégré dans Explorateur de serveurs](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 Le tableau suivant répertorie les types d’objets de données pour chaque type de nœud intégré.

|Type de nœud|Type d’objet de données|
|---------------|----------------------|
|Nœud de site SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Type de contenu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Fonctionnalité|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Champ|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Modèle de liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Mode liste (Microsoft. SharePoint. WebView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Association de flux de travail|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Modèle de flux de travail|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété, consultez [associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Procédure : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procédure : ajouter un nœud SharePoint personnalisé à Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Comment : obtenir des données pour un nœud SharePoint intégré dans Explorateur de serveurs](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Parcourir les connexions SharePoint à l’aide de Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
