---
title: 'Comment : exécuter une commande SharePoint | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 824a747d9253817e1f188730996dac707b3e5ee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-execute-a-sharepoint-command"></a>Comment : exécuter une commande SharePoint
  Si vous souhaitez utiliser le modèle objet serveur dans une extension des outils SharePoint, vous devez créer une personnalisée *commande SharePoint* pour appeler l’API. Une fois que vous définissez la commande et le déployer avec votre extension d’outils SharePoint, votre extension peut exécuter la commande à appeler dans le modèle d’objet serveur SharePoint. Pour exécuter la commande, utilisez une des méthodes de ExecuteCommand un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet.  
  
 Pour plus d’informations sur l’objectif de commandes SharePoint, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Pour exécuter une commande SharePoint  
  
1.  Dans votre extension d’outils SharePoint, obtenez un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet. Le mode d’obtention une <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet varie selon le type d’extension que vous créez :  
  
    -   Dans une extension du système de projet SharePoint, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propriété.  
  
         Pour plus d’informations sur les extensions de système de projet, consultez [extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   Dans une extension de la **connexions SharePoint** nœud **l’Explorateur de serveurs**, utilisez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propriété. Pour obtenir un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> de l’objet, utilisez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propriété.  
  
         Pour plus d’informations sur **l’Explorateur de serveurs** extensions, consultez [extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Dans le code qui ne fait pas partie d’une extension des outils SharePoint, par exemple un Assistant de modèle de projet, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propriété.  
  
         Pour plus d’informations sur la récupération du service de projet, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Appelez l’une des méthodes de ExecuteCommand le <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet. Passez le nom de la commande à exécuter sur le premier argument de la méthode ExecuteCommand. Si votre commande a un paramètre personnalisé, communiquez ce paramètre au deuxième argument de la méthode ExecuteCommand.  
  
     Il existe une surcharge ExecuteCommand différente pour chaque signature de commande pris en charge. Le tableau suivant répertorie les signatures prises en charge et la surcharge à utiliser pour chaque signature.  
  
    |Signature de commande|Surcharge ExecuteCommand à utiliser|  
    |-----------------------|------------------------------------|  
    |La commande a uniquement la valeur par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a uniquement la valeur par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a deux paramètres (la valeur par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre et un paramètre personnalisé) et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a deux paramètres et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> à appeler la surcharge de la `Contoso.Commands.UpgradeSolution` commande qui est décrit dans [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 Le `Execute` méthode illustrée dans cet exemple est une implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> méthode de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interface dans une étape de déploiement personnalisée. Pour voir ce code dans le contexte d’un exemple plus complet, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Notez les détails suivants sur l’appel à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> méthode :  
  
-   Le premier paramètre identifie la commande que vous souhaitez appeler. Cette chaîne correspond à la valeur que vous passez à le <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sur la définition de commande.  
  
-   Le deuxième paramètre est la valeur que vous souhaitez passer au deuxième paramètre personnalisé de la commande. Dans ce cas, il est le chemin d’accès complet du fichier .wsp mis à niveau vers le site SharePoint.  
  
-   Le code ne passe pas implicite <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre à la commande. Ce paramètre est passé à la commande automatiquement lorsque vous appelez la commande à partir d’une extension du système de projet SharePoint ou une extension de la **connexions SharePoint** nœud **l’Explorateur de serveurs**. Dans d’autres types de solutions, comme dans un Assistant de modèle de projet qui implémente le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface, ce paramètre est **null**.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple requiert une référence à l’assembly Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Voir aussi  
 [Appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Procédure pas à pas : extension de l’Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  