---
title: Extension du nœud Connexions SharePoint dans l’Explorateur de serveurs | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7211d31b8e57a88d3f6a5a585e912dd267cf943
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325584"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs
  Dans Visual Studio, vous pouvez vous connecter aux sites SharePoint locaux sur l’ordinateur de développement à l’aide de la **connexions SharePoint** nœud dans le **Explorateur de serveurs** fenêtre. Ce nœud affiche de nombreux composants de sites SharePoint locaux dans une arborescence hiérarchique. Par exemple, vous pouvez afficher les listes, les bibliothèques de documents et les types de contenu sur les sites locaux. Pour plus d’informations sur l’utilisation de **Explorateur de serveurs** pour vous connecter aux sites SharePoint locaux, consultez [SharePoint parcourir les connexions à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Vous pouvez étendre le **connexions SharePoint** nœud en créant des extensions pour les nœuds existants, ou en créant un type de nœud personnalisé et en l’ajoutant à la hiérarchie de nœuds.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Tâches pour l’extension du nœud Connexions SharePoint
 Pour étendre un nœud existant, créez une extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Lorsque vous étendez un nœud, vous pouvez ajouter des fonctionnalités, telles que vos propres éléments de menu contextuel ou les propriétés personnalisées. Pour plus d’informations, consultez [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Pour créer un type de nœud personnalisé, créez une extension Visual Studio qui implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Créer un nœud personnalisé si vous souhaitez afficher les composants de sites SharePoint qui ne sont pas affichés dans **Explorateur de serveurs** par défaut. Par exemple, **Explorateur de serveurs** a-t-il n’affiche pas la galerie WebPart d’un site SharePoint par défaut, mais vous pouvez ajouter un nœud personnalisé qui s’en charge. Pour plus d’informations, consultez [Comment : ajouter un nœud SharePoint personnalisé à l’Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) et [procédure pas à pas : étendre des Explorateur de serveurs aux composants WebPart d’affichage](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="add-custom-properties-to-nodes"></a>Ajouter des propriétés personnalisées aux nœuds
 Lorsque vous étendez un nœud ou créez un type de nœud personnalisés, vous pouvez ajouter des propriétés personnalisées au nœud. Les propriétés s’affichent dans le **propriétés** fenêtre lorsque le nœud est sélectionné.  
  
 Il existe deux types de propriétés personnalisées, que vous pouvez ajouter à un nœud :  
  
-   Propriétés qui affichent un jeu de données en lecture seule à partir du site SharePoint. Les données décrivent le composant SharePoint que le nœud représente. Pour une procédure pas à pas qui montre comment effectuer cette opération, consultez [procédure pas à pas : étendre des Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Propriétés qui affichent les données en lecture/écriture personnalisé. Pour obtenir un exemple de code qui montre comment effectuer cette opération, consultez [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="get-data-for-built-in-nodes"></a>Obtenir des données pour les nœuds intégrés
 Tous les nœuds intégrés fournis par Visual Studio incluent des données relatives au composant SharePoint qu’ils représentent. Par exemple, un nœud qui représente une liste sur le site SharePoint fournit des données sur la liste, comme le titre et l’URL de la vue par défaut pour la liste.  
  
 Pour accéder à ces données, récupérer un objet de données à partir de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet qui représente le nœud qui vous intéresse. Le type de l’objet de données varie selon le type du nœud.  
  
 L’exemple de code suivant montre comment obtenir l’objet de données pour un nœud de la liste. Pour voir cet exemple dans le contexte d’un exemple plus complet, consultez [Comment : obtenir des données pour un nœud SharePoint intégré dans l’Explorateur de serveurs](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 Le tableau suivant répertorie les types d’objet de données pour chaque type de nœud intégré.  
  
|Type de nœud|Type d’objet de données|  
|---------------|----------------------|  
|Nœud de site SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Type de contenu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Fonctionnalité|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Champ|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Modèle de liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Affichage de liste (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Association de flux de travail|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Modèle de flux de travail|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Pour plus d’informations sur l’utilisation de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriété, consultez [associer des données personnalisées à SharePoint extensions d’outils](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Comment : ajouter un nœud SharePoint personnalisé à l’Explorateur de serveurs](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Comment : obtenir des données pour un nœud SharePoint intégré dans l’Explorateur de serveurs](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associer des données personnalisées avec les extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Parcourir les connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  
