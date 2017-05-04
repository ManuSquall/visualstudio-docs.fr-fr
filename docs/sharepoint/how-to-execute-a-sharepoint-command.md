---
title: "How to: Execute a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  Si vous souhaitez appliquer le modèle d'objet serveur à une extension d'outils SharePoint, vous devez créer une *commande SharePoint* personnalisée pour appeler l'API.  Une fois que vous avez défini la commande et que vous l'avez déployée avec votre extension d'outils SharePoint, l'extension peut exécuter la commande pour effectuer un appel dans le modèle d'objet serveur SharePoint.  Pour exécuter la commande, utilisez l'une des méthodes ExecuteCommand d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Pour plus d'informations sur la finalité des commandes SharePoint, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Pour exécuter une commande SharePoint  
  
1.  Dans votre extension d'outils SharePoint, obtenez un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  Le mode d'obtention d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> dépend du type d'extension que vous créez :  
  
    -   Dans une extension du système de projet SharePoint, utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>.  
  
         Pour plus d'informations sur les extensions de système de projet, consultez [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   Dans une extension du nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**, utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>.  Pour obtenir un objet <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>, utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>.  
  
         Pour plus d'informations sur les extensions de l'**Explorateur de serveurs**, consultez [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Dans un code qui ne fait pas partie d'une extension des outils SharePoint, comme dans un Assistant Modèle de projet, utilisez la propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.  
  
         Pour plus d'informations au sujet de la récupération du service du projet, consultez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Appelez l'une des méthodes ExecuteCommand de l'objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  Communiquez le nom de la commande que vous souhaitez exécuter au premier argument de la méthode ExecuteCommand.  Si votre commande a un paramètre personnalisé, communiquez ce paramètre au deuxième argument de la méthode ExecuteCommand.  
  
     La surcharge ExecuteCommand n'est pas la même pour chaque signature de commande prise en charge.  Le tableau suivant répertorie les signatures prises en charge et la surcharge qu'il convient d'utiliser pour chaque signature.  
  
    |Signature de commande|Surcharge ExecuteCommand à utiliser|  
    |---------------------------|-----------------------------------------|  
    |La commande possède uniquement le paramètre par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande possède uniquement le paramètre par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a deux paramètres \(le paramètre par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> et un paramètre personnalisé\) et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a deux paramètres et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser la surcharge <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> pour appeler la commande `Contoso.Commands.UpgradeSolution` décrite dans [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 La méthode `Execute` affichée dans cet exemple est une implémentation de la méthode <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> de l'interface <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> dans une étape de déploiement personnalisée.  Pour voir ce code dans le contexte d'une procédure pas à pas plus vaste, consultez [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Tenez compte des remarques suivantes au sujet de l'appel de la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> :  
  
-   Le premier paramètre identifie la commande que vous souhaitez appeler.  Cette chaîne correspond à la valeur transmise à l'attribut <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sur la définition de commande.  
  
-   Le deuxième paramètre est la valeur que vous souhaitez communiquer au deuxième paramètre personnalisé de la commande.  Dans ce cas, il s'agit du chemin d'accès complet du fichier .wsp mis à niveau vers le site SharePoint.  
  
-   Le code ne fournit pas le paramètre <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implicite à la commande.  Ce paramètre est communiqué automatiquement à la commande lorsque vous appelez celle\-ci à partir d'une extension du système de projet SharePoint ou d'une extension du nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.  Dans d'autres types de solution, comme dans un Assistant Modèle de projet prévu pour implémenter l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, ce paramètre est **null**.  
  
## Compilation du code  
 Cet exemple requiert une référence à l'assembly Microsoft.VisualStudio.SharePoint.  
  
## Voir aussi  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  