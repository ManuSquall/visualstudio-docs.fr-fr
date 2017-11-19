---
title: "Comment : exécuter Code lorsqu’un projet SharePoint est déployé ou le retrait | Documents Microsoft"
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
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0650bfdb7961728fed34147c05f6333d8255e373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Comment : exécuter du code lors du déploiement ou du retrait d'un projet SharePoint
  Si vous souhaitez effectuer des tâches supplémentaires lorsqu’un projet SharePoint est déployé ou retiré, vous pouvez gérer les événements déclenchés par Visual Studio. Pour plus d’informations, consultez [étendre un empaquetage SharePoint et déploiement](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Pour exécuter du code lorsqu’un projet SharePoint est déployé ou retiré  
  
1.  Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
    -   [Guide pratique pour créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Guide pratique pour créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Guide pratique pour définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Dans l’extension, accédez à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet. Pour plus d’informations, consultez [Comment : récupérer le Service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> les événements du service de projet.  
  
4.  Événements dans les gestionnaires, utilisez le <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> pour obtenir plus d’informations sur la session de déploiement actuelle. Par exemple, vous pouvez déterminer quel projet est dans la session de déploiement actuelle et si elle est en cours déployée ou retirée.  
  
 L’exemple de code suivant montre comment gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> événements dans une extension de projet. Cette extension écrit un message supplémentaire à la **sortie** fenêtre lorsque le déploiement démarre et se termine pour un projet SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Déploiement de l’Extension  
 Pour déployer l’extension, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement et l’extension empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Guide pratique pour exécuter le code lors de l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  