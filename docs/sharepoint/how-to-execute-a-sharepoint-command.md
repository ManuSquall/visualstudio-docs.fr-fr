---
title: 'Comment : exécuter une commande SharePoint | Microsoft Docs'
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
ms.openlocfilehash: ce195dd34c7c0b509f9de4cbe2cfd14d9a477f87
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119226"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Comment : exécuter une commande SharePoint
  Si vous souhaitez utiliser le modèle objet serveur dans une extension des outils SharePoint, vous devez créer un personnalisé *commande SharePoint* pour appeler l’API. Une fois que vous définissez la commande et le déployez avec votre extension des outils SharePoint, votre extension peut exécuter la commande à appeler dans le modèle d’objet serveur SharePoint. Pour exécuter la commande, utilisez une des méthodes de ExecuteCommand un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet.  
  
 Pour plus d’informations sur la finalité des commandes SharePoint, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Pour exécuter une commande SharePoint  
  
1.  Dans votre extension des outils SharePoint, obtenez un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet. Le cas, vous obtenez un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet varie selon le type d’extension que vous créez :  
  
    -   Dans une extension du système de projet SharePoint, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propriété.  
  
         Pour plus d’informations sur les extensions de système de projet, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   Dans une extension de la **connexions SharePoint** nœud **Explorateur de serveurs**, utilisez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propriété. Pour obtenir un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> de l’objet, utilisez le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propriété.  
  
         Pour plus d’informations sur **Explorateur de serveurs** extensions, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   Dans le code qui ne fait pas partie d’une extension des outils SharePoint, par exemple un Assistant modèle de projet, utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propriété.  
  
         Pour plus d’informations sur la récupération du service de projet, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Appelez une des méthodes de ExecuteCommand le <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet. Passez le nom de la commande à exécuter pour le premier argument de la méthode ExecuteCommand. Si votre commande a un paramètre personnalisé, passez ce paramètre au deuxième argument de la méthode ExecuteCommand.  
  
     Il existe une surcharge ExecuteCommand différents pour chaque signature de commande pris en charge. Le tableau suivant répertorie les signatures prises en charge et la surcharge à utiliser pour chaque signature.  
  
    |Signature de commande|Surcharge ExecuteCommand à utiliser|  
    |-----------------------|------------------------------------|  
    |La commande a uniquement la valeur par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a uniquement la valeur par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a deux paramètres (la valeur par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre et un paramètre personnalisé) et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |La commande a deux paramètres et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> surcharge pour appeler le `Contoso.Commands.UpgradeSolution` commande qui est décrite dans [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 Le `Execute` méthode illustrée dans cet exemple est une implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> méthode de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interface dans une étape de déploiement personnalisé. Pour voir ce code dans le contexte d’un exemple plus complet, consultez [procédure pas à pas : créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Notez les points suivants à propos de l’appel à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> méthode :  
  
-   Le premier paramètre identifie la commande que vous souhaitez appeler. Cette chaîne correspond à la valeur que vous passez à la <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sur la définition de commande.  
  
-   Le deuxième paramètre est la valeur que vous souhaitez passer au second paramètre de la commande personnalisé. Dans ce cas, il est le chemin d’accès complet de le *.wsp* fichier est mis à niveau vers le site SharePoint.  
  
-   Le code ne passe pas le caractère implicite <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> paramètre à la commande. Ce paramètre est passé dans la commande automatiquement quand vous appelez la commande à partir d’une extension du système de projet SharePoint ou une extension de la **connexions SharePoint** nœud **Explorateur de serveurs**. Dans d’autres types de solutions, comme dans un Assistant de modèle de projet qui implémente le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface, ce paramètre est **null**.  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple requiert une référence à l’assembly Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Voir aussi
 [Appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
