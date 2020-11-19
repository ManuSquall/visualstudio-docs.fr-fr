---
title: 'Comment : exécuter une commande SharePoint | Microsoft Docs'
description: Découvrez comment créer une commande SharePoint personnalisée pour appeler l’API du modèle objet serveur à partir d’une extension d’outils SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2746704e30a61b0971db50a5083855b4a93560d4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903533"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Comment : exécuter une commande SharePoint
  Si vous souhaitez utiliser le modèle d’objet serveur dans une extension d’outils SharePoint, vous devez créer une *commande SharePoint* personnalisée pour appeler l’API. Une fois que vous avez défini la commande et que vous l’avez déployée avec votre extension d’outils SharePoint, votre extension peut exécuter la commande pour appeler le modèle d’objet serveur SharePoint. Pour exécuter la commande, utilisez l’une des méthodes ExecuteCommand d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet.

 Pour plus d’informations sur l’objectif des commandes SharePoint, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Pour exécuter une commande SharePoint

1. Dans votre extension d’outils SharePoint, récupérez un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet. La façon dont vous récupérez un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet dépend du type d’extension que vous créez :

    - Dans une extension du système de projet SharePoint, utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propriété.

         Pour plus d’informations sur les extensions système de projet, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - Dans une extension du nœud **Connexions SharePoint** dans **Explorateur de serveurs**, utilisez la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propriété. Pour récupérer un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> objet, utilisez la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propriété.

         Pour plus d’informations sur les extensions de **Explorateur de serveurs** , consultez [étendre le nœud connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - Dans le code qui ne fait pas partie d’une extension des outils SharePoint, tel qu’un Assistant modèle de projet, utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propriété.

         Pour plus d’informations sur la récupération du service de projet, consultez [utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Appelez l’une des méthodes ExecuteCommand de l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objet. Transmettez le nom de la commande que vous souhaitez exécuter au premier argument de la méthode ExecuteCommand. Si votre commande a un paramètre personnalisé, transmettez ce paramètre au deuxième argument de la méthode ExecuteCommand.

     Il existe une surcharge ExecuteCommand différente pour chaque signature de commande prise en charge. Le tableau suivant répertorie les signatures prises en charge et la surcharge à utiliser pour chaque signature.

    |Signature de la commande|Surcharge de la valeur ExecuteCommand à utiliser|
    |-----------------------|------------------------------------|
    |La commande a uniquement le paramètre par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |La commande a uniquement le paramètre par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |La commande a deux paramètres (le paramètre par défaut <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> et un paramètre personnalisé) et aucune valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |La commande a deux paramètres et une valeur de retour.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> surcharge pour appeler la `Contoso.Commands.UpgradeSolution` commande décrite dans [How to : Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 La `Execute` méthode illustrée dans cet exemple est une implémentation de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> méthode de l' <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interface dans une étape de déploiement personnalisée. Pour voir ce code dans le contexte d’un exemple plus complet, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Notez les détails suivants relatifs à l’appel de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> méthode :

- Le premier paramètre identifie la commande que vous souhaitez appeler. Cette chaîne correspond à la valeur que vous transmettez au <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sur la définition de la commande.

- Le deuxième paramètre est la valeur que vous souhaitez passer au deuxième paramètre personnalisé de la commande. Dans ce cas, il s’agit du chemin d’accès complet du fichier *. wsp* qui est mis à niveau vers le site SharePoint.

- Le code ne passe pas le paramètre implicite <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> à la commande. Ce paramètre est transmis automatiquement à la commande lorsque vous appelez la commande à partir d’une extension du système de projet SharePoint ou d’une extension du nœud **Connexions SharePoint** dans **Explorateur de serveurs**. Dans d’autres types de solutions, comme dans un Assistant modèle de projet qui implémente l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface, ce paramètre a la **valeur null**.

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple requiert une référence à l’assembly Microsoft. VisualStudio. SharePoint.

## <a name="see-also"></a>Voir aussi
- [Appeler les modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
