---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer"
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
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  Pour chaque nœud SharePoint intégré dans l'**Explorateur de serveurs**, vous pouvez obtenir des données pour le composant SharePoint sous\-jacent que le nœud représente.  Pour plus d'informations, consultez [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Exemple  
 L'exemple de code suivant montre comment obtenir des données pour la liste SharePoint sous\-jacente qu'un nœud de liste représente dans l'**Explorateur de serveurs**.  Par défaut, les nœuds de liste ont un élément de menu contextuel **Afficher dans le navigateur** sur lequel vous pouvez cliquer pour ouvrir les listes dans un navigateur Web.  Cet exemple étend les nœuds de liste en ajoutant un élément de menu contextuel **Afficher dans Visual Studio**, qui ouvre directement les listes dans Visual Studio.  Le code accède aux données de liste pour le nœud afin d'obtenir l'URL de la liste à ouvrir dans Visual Studio.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 Cet exemple utilise le service de projet SharePoint pour obtenir l'objet <xref:EnvDTE.DTE> utilisé afin d'ouvrir les listes dans Visual Studio.  Pour plus d'informations au sujet du service de projet SharePoint, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Pour plus d'informations sur les tâches de base permettant de créer une extension pour un nœud SharePoint, consultez [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension **Explorateur de serveurs**, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  