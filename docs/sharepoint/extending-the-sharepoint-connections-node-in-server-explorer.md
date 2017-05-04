---
title: "Extending the SharePoint Connections Node in Server Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  Dans Visual Studio, vous pouvez vous connecter aux sites sharepoint locaux sur l'ordinateur de développement via le nœud de **Connexions SharePoint** dans la fenêtre d'**Explorateur de serveurs** .  Ce nœud présente un grand nombre de composants de sites SharePoint locaux dans une arborescence hiérarchique.  Par exemple, vous pouvez consulter les listes, bibliothèques de documents et types de contenu sur les sites locaux. Pour plus d'informations sur l'utilisation de l'**Server Explorer** pour se connecter aux sites SharePoint locaux, consultez [Parcours des connexions SharePoint à l'aide de l'Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Vous pouvez étendre le nœud **Connexions SharePoint** en créant des extensions pour les nœuds existants, ou en créant un type de nœud personnalisé et en l'ajoutant à la hiérarchie de nœuds.  
  
## Tâches permettant l'extension du nœud Connexions SharePoint  
 Pour étendre un nœud existant, créez une extension Visual Studio qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Lorsque vous étendez un nœud, vous pouvez lui ajouter des fonctionnalités, telles que vos propres éléments de menu contextuel ou propriétés personnalisées.  Pour plus d'informations, consultez [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Pour créer un type de nœud personnalisé, créez une extension Visual Studio qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Créez un nœud personnalisé si vous comptez afficher les composants des sites SharePoint qui ne sont pas affichés par défaut dans l'**Explorateur de serveurs**.  Il faut savoir, par exemple, que l'**Explorateur de serveurs** n'affiche pas par défaut la galerie de composants WebPart d'un site SharePoint, mais rien ne vous empêche de prévoir un nœud personnalisé à cet effet.  Pour plus d'informations, consultez [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) et [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Ajout de propriétés personnalisées aux nœuds  
 Lorsque vous étendez un nœud ou créez un type de nœud personnalisé, vous pouvez lui ajouter des propriétés personnalisées.  Les propriétés apparaissent dans la fenêtre **Propriétés** lorsque le nœud est sélectionné.  
  
 Il existe deux types de propriétés personnalisées que vous pouvez ajouter à un nœud :  
  
-   Propriétés qui affichent un jeu de données en lecture seule du site SharePoint.  Les données décrivent le composant SharePoint représenté par le nœud.  Pour obtenir une procédure pas à pas illustrant ce processus, consultez [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Propriétés qui affichent des données personnalisées en lecture\/écriture.  Pour obtenir un exemple de code qui illustre cette opération, consultez [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Obtention de données pour les nœuds intégrés  
 Tous les nœuds intégrés fournis par Visual Studio incluent des données relatives au composant SharePoint qu'ils représentent.  Par exemple, un nœud qui représente une liste sur le site SharePoint fournit des données sur cette liste, telles que le titre et l'URL de la vue par défaut de la liste.  
  
 Pour accéder à ces données, extrayez un objet de données de la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> de l'objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> qui représente le nœud qui vous intéresse.  Le type de l'objet de données dépend du type du nœud.  
  
 L'exemple de code suivant montre comment obtenir l'objet de données pour un nœud de liste.  Pour voir cet exemple dans le contexte d'une procédure pas à pas plus vaste, consultez [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 Le tableau suivant répertorie les types d'objets de données pour chaque type de nœud intégré.  
  
|Type de nœud|Type d'objet de données|  
|------------------|-----------------------------|  
|Nœud de site SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Type de contenu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Fonctionnalité|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Champ|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Modèle de liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Vue Liste \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Association de flux de travail|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Modèle de flux de travail|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Pour plus d'informations sur l'utilisation de la propriété <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, consultez [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Voir aussi  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Parcours des connexions SharePoint à l'aide de l'Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  