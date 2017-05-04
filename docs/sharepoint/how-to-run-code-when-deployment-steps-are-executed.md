---
title: "How to: Run Code When Deployment Steps are Executed | Microsoft Docs"
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
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# How to: Run Code When Deployment Steps are Executed
  Si vous souhaitez effectuer des tâches supplémentaires pour une étape du déploiement dans un projet SharePoint, il est possible de gérer des événements déclenchés par des éléments de projet SharePoint avant et après l'exécution de chaque étape de déploiement par Visual Studio.  Pour plus d'informations, consultez [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Pour exécuter le code lors de l'exécution des étapes de déploiement  
  
1.  Créez une extension d'élément de projet, une extension de projet ou une définition d'un nouveau type d'élément de projet.  Pour plus d'informations, consultez les rubriques suivantes :  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Dans l'extension, gérez les événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> \(dans une extension d'élément de projet ou une extension de projet\) ou d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> \(dans une définition d'un nouveau type d'élément de projet\).  
  
3.  Dans les gestionnaires d'événements, utilisez les paramètres <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> et <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> pour obtenir des informations à propos de l'étape de déploiement.  Vous pouvez, par exemple, déterminer l'étape du déploiement en cours d'exécution et savoir si la solution est déployée ou retirée.  
  
## Exemple  
 L'exemple de code suivant montre comment gérer les événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> dans une extension pour l'élément de projet Instance de liste.  Cette extension écrit un message supplémentaire dans la fenêtre **Sortie** lorsque Visual Studio recycle le pool d'applications pendant le déploiement et le retrait de la solution.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/handledeploymentstepevents.cs#4)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/handledeploymentstepevents.vb#4)]  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  