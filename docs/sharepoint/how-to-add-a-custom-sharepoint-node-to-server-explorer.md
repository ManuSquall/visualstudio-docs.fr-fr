---
title: "How to: Add a Custom SharePoint Node to Server Explorer"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  Il est possible d'insérer des nœuds personnalisés sous le nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.  Cela peut être utile si vous comptez afficher des composants SharePoint supplémentaires qui n'apparaissent pas par défaut dans l'**Explorateur de serveurs**.  Pour plus d'informations, consultez [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Pour ajouter un nœud personnalisé, commencez par créer une classe qui définit le nouveau nœud.  Créez ensuite une extension ayant pour effet d'ajouter le nœud comme un enfant d'un nœud existant.  
  
### Pour définir le nouveau nœud  
  
1.  Créez un projet Bibliothèque de classes.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Créez une classe qui implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Ajouter les attributs suivants à la classe :  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Cet attribut permet à Visual Studio de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Communiquez le type <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> au constructeur d'attribut.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  Dans une définition de nœud, cet attribut spécifie l'identificateur de chaîne pour le nouveau nœud.  Nous vous recommandons de respecter le format *NomSociété**NomNœud* pour garantir un identificateur unique à tous les nœuds.  
  
5.  Dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>, utilisez les membres du paramètre *typeDefinition* pour définir le comportement du nouveau nœud.  Ce paramètre est un objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> qui fournit l'accès aux événements définis dans l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  
  
     L'exemple de code suivant montre comment définir un nouveau nœud.  Cet exemple suppose que votre projet contient une icône nommée CustomChildNodeIcon sous forme de ressource incorporée.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### Pour ajouter le nouveau nœud comme enfant d'un nœud existant  
  
1.  Dans le même projet que votre définition de nœud, créez une classe permettant d'implémenter l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
2.  Ajoutez l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe.  Cet attribut permet à Visual Studio de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Passez le type <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> au constructeur d'attribut.  
  
3.  Ajoutez l'attribut <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à la classe.  Dans une extension de nœud, cet attribut spécifie l'identificateur de chaîne du type de nœud que vous souhaitez étendre.  
  
     Pour spécifier les types de nœuds intégrés fournis par Visual Studio, passez l'une des valeurs d'énumération suivantes au constructeur d'attribut :  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes> : utilisez ces valeurs pour spécifier des nœuds de connexion de site \(nœuds qui affichent les URL de site\), des nœuds de site ou tous les autres nœuds parents de l'**Explorateur de serveurs**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes> : Utilisez ces valeurs pour spécifier l'un des nœuds intégrés qui représentent un composant individuel sur un site SharePoint, tel qu'un nœud qui représente une liste, un champ ou un type de contenu.  
  
4.  Dans votre implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>, gérez l'événement <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> du paramètre <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>.  
  
5.  Dans le gestionnaire d'événements <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>, ajoutez le nouveau nœud à la collection de nœuds enfants de l'objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> exposé par le paramètre d'arguments d'événement.  
  
     L'exemple de code suivant montre comment ajouter le nouveau nœud en tant qu'enfant du nœud du site SharePoint dans l'**Explorateur de serveurs**.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## Exemple complet  
 L'exemple de code suivant fournit le code complet permettant de définir un nœud simple et de l'ajouter en tant qu'enfant du nœud du site SharePoint dans l'**Explorateur de serveurs**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## Compilation du code  
 Cet exemple suppose que votre projet contient une icône nommée CustomChildNodeIcon sous forme de ressource incorporée.  Cet exemple nécessite également des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## Déploiement de l'extension  
 Pour déployer l'extension **Explorateur de serveurs**, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  