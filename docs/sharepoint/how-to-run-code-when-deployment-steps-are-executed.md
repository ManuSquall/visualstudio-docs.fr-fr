---
title: "Comment : exécuter Code lors des étapes de déploiement sont exécutées | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e1aed7e4fe7ee30450b3ec37ce36616648e830fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Comment : exécuter le code lors de l'exécution des étapes de déploiement
  Si vous souhaitez effectuer des tâches supplémentaires pour une étape de déploiement dans un projet SharePoint, vous pouvez gérer les événements qui sont déclenchés par les éléments de projet SharePoint avant et après chaque étape de déploiement de l’exécution de Visual Studio. Pour plus d’informations, consultez [étendre un empaquetage SharePoint et déploiement](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Pour exécuter du code lors de l’exécution des étapes de déploiement  
  
1.  Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
    -   [Guide pratique pour créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Guide pratique pour créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Guide pratique pour définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Dans l’extension, gérez les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> événements d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objet (dans une extension d’élément de projet ou une extension de projet) ou un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objet (dans une définition d’un nouveau type d’élément de projet).  
  
3.  Événements dans les gestionnaires, utilisez le <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> et <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> paramètres pour obtenir des informations sur l’étape de déploiement. Par exemple, vous pouvez déterminer l’étape de déploiement qui s’exécute et indique si la solution est déployée ou retirée.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> événements dans une extension pour l’élément de projet d’Instance de liste. Cette extension écrit un message supplémentaire à la **sortie** fenêtre lorsque Visual Studio recycle le pool d’applications pendant le déploiement et le retrait de la solution.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement et l’extension empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Procédure pas à pas : Création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Guide pratique pour exécuter du code lors du déploiement ou du retrait d’un projet SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  