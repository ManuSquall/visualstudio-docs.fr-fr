---
title: "How to: Run Code When a SharePoint Project is Deployed or Retracted"
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
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Run Code When a SharePoint Project is Deployed or Retracted
  Si vous souhaitez effectuer des tâches supplémentaires lorsqu'un projet SharePoint est déployé ou retiré, vous pouvez gérer des événements déclenchés par Visual Studio.  Pour plus d'informations, consultez [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Pour exécuter du code lors du déploiement ou du retrait d'un projet SharePoint  
  
1.  Créez une extension d'élément de projet, une extension de projet ou une définition d'un nouveau type d'élément de projet.  Pour plus d'informations, consultez les rubriques suivantes :  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Dans l'extension, accédez à l'objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  Pour plus d'informations, consultez [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Gérez les événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> du service du projet.  
  
4.  Dans les gestionnaires d'événements, utilisez le paramètre <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> pour obtenir des informations à propos de la session de déploiement actuelle.  Vous pouvez, par exemple, déterminer le projet dans la session de déploiement actuelle et savoir s'il est déployé ou retiré.  
  
 L'exemple de code suivant illustre la gestion des événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> dans une extension de projet.  Cette extension écrit un message supplémentaire dans la fenêtre **Sortie** lorsque le déploiement démarre et se termine pour un projet SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handleprojectdeploymentevents.vb#12)]  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  