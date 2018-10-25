---
title: 'Comment : exécuter Code lorsqu’un projet SharePoint est déployé ou du retrait | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: da1b6dd4ff71bcc78043ea88c8f833b9c0f32a38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832444"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Comment : exécuter du code quand un projet SharePoint est déployé ou retiré
  Si vous souhaitez effectuer des tâches supplémentaires lorsqu’un projet SharePoint est déployé ou retiré, vous pouvez gérer les événements qui sont déclenchés par Visual Studio. Pour plus d’informations, consultez [SharePoint étendre empaquetage et déploiement](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Pour exécuter du code quand un projet SharePoint est déployé ou retiré  
  
1. Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
   -   [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
   -   [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
   -   [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2. Dans l’extension, accédez à la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet. Pour plus d’informations, consultez [Comment : récupérer le service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3. Gérer le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> événements du service de projet.  
  
4. Dans les événements gestionnaires, utilisez le <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> pour obtenir des informations sur la session de déploiement actuelle. Par exemple, vous pouvez déterminer quel projet se trouve dans la session de déploiement actuelle et si elle est en cours de déploiement ou de retrait.  
  
   L’exemple de code suivant montre comment gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> événements dans une extension de projet. Cette extension écrit un message supplémentaire pour le **sortie** fenêtre lorsque le déploiement démarre et se termine pour un projet SharePoint.  
  
   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Déployer l’extension  
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi
 [Étendre le déploiement et empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Comment : exécuter du code quand l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
