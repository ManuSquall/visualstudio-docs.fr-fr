---
title: "How to: Extend a SharePoint Node in Server Explorer | Microsoft Docs"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  Il est possible d'étendre des nœuds sous le nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.  Cela est utile lorsque vous souhaitez ajouter de nouveaux nœuds enfants, éléments de menu contextuel ou propriétés à un nœud existant.  Pour plus d'informations, consultez [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### Pour étendre un nœud SharePoint dans l'Explorateur de serveurs  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Créez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Ajoutez l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe.  Cet attribut permet à Visual Studio de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Passez le type <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> au constructeur d'attribut.  
  
5.  Ajoutez l'attribut <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à la classe.  Cet attribut spécifie l'identificateur de chaîne pour le type de nœud que vous souhaitez étendre.  
  
     Pour spécifier les types de nœuds intégrés fournis par Visual Studio, passez l'une des valeurs d'énumération suivantes au constructeur d'attribut :  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes> : utilisez ces valeurs pour spécifier des nœuds de connexion de site \(nœuds qui affichent les URL de site\), des nœuds de site ou tous les autres nœuds parents de l'**Explorateur de serveurs**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes> : Utilisez ces valeurs pour spécifier l'un des nœuds intégrés qui représentent un composant individuel sur un site SharePoint, tel qu'un nœud qui représente une liste, un champ ou un type de contenu.  
  
6.  Dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>, utilisez les membres du paramètre *nodeType* pour ajouter des fonctionnalités au nœud.  Ce paramètre est un objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> qui fournit l'accès aux événements définis dans l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  Par exemple, il est possible de gérer les événements suivants :  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> : Gérez cet événement pour ajouter de nouveaux nœuds enfants au nœud.  Pour plus d'informations, consultez [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested> : Gérez cet événement pour ajouter un élément de menu contextuel personnalisé au nœud.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested> : Gérez cet événement pour ajouter des propriétés personnalisées au nœud.  Les propriétés apparaissent dans la fenêtre **Propriétés** lorsque le nœud est sélectionné.  
  
## Exemple  
 L'exemple de code suivant montre comment créer deux types différents d'extensions de nœud :  
  
-   Une extension qui ajoute un élément de menu contextuel aux nœuds de site SharePoint.  Lorsque vous cliquez sur l'élément de menu, il affiche le nom du nœud sur lequel vous avez cliqué.  
  
-   Une extension qui ajoute une propriété personnalisée nommée **ContosoExampleProperty** à chaque nœud qui représente un champ nommé **Corps**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 Cette extension ajoute aux nœuds une propriété de type chaîne modifiable.  Vous pouvez également créer des propriétés personnalisées qui affichent des données en lecture seule à partir du serveur SharePoint.  Pour obtenir un exemple qui illustre cette opération, consultez [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## Déploiement de l'extension  
 Pour déployer l'extension **Explorateur de serveurs**, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  