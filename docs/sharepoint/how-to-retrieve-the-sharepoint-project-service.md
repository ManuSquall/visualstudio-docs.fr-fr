---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  Vous pouvez accéder au service du projet SharePoint dans les types de solution suivants :  
  
-   Extension du système de projet SharePoint, telle qu'une extension de projet, une extension d'élément de projet ou une définition de type d'élément de projet.  Pour plus d'informations sur ces types d'extensions, consultez [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Une extension du nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.  Pour plus d'informations sur ces types d'extensions, consultez [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Un autre type d'extension Visual Studio, tel qu'un complément ou un VSPackage.  
  
## Extraction du service dans les extensions de système de projet  
 Dans toute extension du système de projet SharePoint, vous pouvez accéder au service du projet à l'aide de la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  
  
 Il est également possible d'extraire le service du projet en procédant selon les façons suivantes.  
  
#### Pour extraire le service dans une extension de projet  
  
1.  Dans votre implémentation de l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>, localisez la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  
  
2.  Utilisez le paramètre *projectService* pour accéder au service.  
  
     L'exemple de code suivant montre comment utiliser le service du projet pour écrire un message dans la fenêtre **Sortie** et la fenêtre **Liste d'erreurs** dans une extension de projet simple.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     Pour plus d'informations sur la création d'extensions de projet, consultez [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### Pour extraire le service dans une extension d'élément de projet  
  
1.  Dans votre implémentation de l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, localisez la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  
  
2.  Utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> du paramètre *projectItemType* pour extraire le service.  
  
     L'exemple de code suivant montre comment utiliser le service du projet pour écrire un message dans la fenêtre **Sortie** et la fenêtre **Liste d'erreurs** dans une extension simple de l'élément de projet **Définition de liste**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     Pour plus d'informations sur la création d'extensions d'élément, consultez [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### Pour extraire le service dans une définition de type d'élément de projet  
  
1.  Dans votre implémentation de l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, localisez la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  
  
2.  Utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> du paramètre *typeDefinition* pour extraire le service.  
  
     L'exemple de code suivant montre comment utiliser le service du projet pour écrire un message dans la fenêtre **Sortie** et la fenêtre **Liste d'erreurs** dans une définition de type d'élément de projet simple.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     Pour plus d'informations sur la définition de types d'élément de projet, consultez [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Extraction du service dans les extensions de l'Explorateur de serveurs  
 Dans une extension du nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**, vous pouvez accéder au service du projet à l'aide de la propriété <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>.  
  
#### Pour extraire le service dans une extension de l'Explorateur de serveurs  
  
1.  Obtenez un objet <xref:System.IServiceProvider> de la propriété <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> dans votre extension.  
  
2.  Utilisez la méthode <xref:System.IServiceProvider.GetService%2A> pour demander un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
     L'exemple de code suivant montre comment utiliser le service du projet pour écrire un message dans la fenêtre **Sortie** et la fenêtre **Liste d'erreurs** dans un menu contextuel que l'extension ajoute afin de répertorier des nœuds dans l'**Explorateur de serveurs**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     Pour plus d'informations sur l'extension du nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**, consultez [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Extraction du service dans d'autres extensions Visual Studio  
 Vous pouvez extraire le service du projet dans un VSPackage ou dans toute extension Visual Studio qui a accès à un objet <xref:EnvDTE80.DTE2> dans le modèle d'objet Automation, comme un complément ou un Assistant Modèle de projet qui implémente l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
 Dans un VSPackage, vous pouvez demander un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> à l'aide de l'une des méthodes suivantes :  
  
-   Méthode <xref:System.IServiceProvider.GetService%2A> d'un VSPackage managé qui dérive de la classe <xref:Microsoft.VisualStudio.Shell.Package>.  Pour plus d'informations, consultez [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md).  
  
-   Méthode <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> statique.  Pour plus d'informations, consultez [Procédure : utilisation d’un GetGlobalService](../Topic/How%20to:%20Use%20GetGlobalService.md).  
  
 Dans une extension Visual Studio qui a accès à un objet <xref:EnvDTE80.DTE2>, vous pouvez demander un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> à l'aide de la méthode <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> d'un objet <xref:Microsoft.VisualStudio.Shell.ServiceProvider>.  Pour plus d'informations, consultez [Comment : obtenir un service à partir de l’objet DTE](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md).  
  
### Exemple  
 L'exemple de code suivant montre comment extraire le service du projet dans un complément Visual Studio.  Pour utiliser ce code, exécutez\-le à partir de la classe `Connect` dans un projet de complément.  L'objet `_applicationObject` est généré automatiquement dans les projets de complément ; cet objet est une instance de l'interface <xref:EnvDTE80.DTE2>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 Cet exemple nécessite :  
  
-   Projet de complément Visual Studio.  Pour plus d'informations, consultez [Comment : créer un complément](../Topic/How%20to:%20Create%20an%20Add-In.md).  
  
-   Références aux assemblys Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell et Microsoft.VisualStudio.SharePoint.  
  
## Voir aussi  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Comment : créer un complément](../Topic/How%20to:%20Create%20an%20Add-In.md)   
 [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Comment : obtenir un service à partir de l’objet DTE](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md)   
 [Comment : utiliser des Assistants avec des modèles de projet](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  