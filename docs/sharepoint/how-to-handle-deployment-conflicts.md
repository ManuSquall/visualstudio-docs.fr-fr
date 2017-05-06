---
title: "How to: Handle Deployment Conflicts"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Handle Deployment Conflicts
  Vous pouvez fournir votre propre code pour traiter des conflits de déploiement d'un élément de projet SharePoint.  Par exemple, vous pouvez déterminer si des fichiers dans l'élément de projet en cours existent déjà à l'emplacement du déploiement, puis supprimer les fichiers déployés avant que l'élément de projet en cours ne soit déployé.  Pour plus d'informations sur les conflits de déploiement, consultez [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### Pour traiter un conflit de déploiement  
  
1.  Créez une extension d'élément de projet, une extension de projet ou une définition d'un nouveau type d'élément de projet.  Pour plus d'informations, consultez les rubriques suivantes :  
  
    -   [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Dans l'extension, traitez l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> \(dans une extension d'élément de projet ou une extension de projet\) ou d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> \(dans une définition d'un nouveau type d'élément de projet\).  
  
3.  Dans le gestionnaire d'événements, identifiez un conflit entre l'élément de projet en cours de déploiement et la solution déployée sur le site SharePoint, selon les critères qui s'appliquent à votre scénario.  Vous pouvez utiliser la propriété <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> du paramètre d'arguments d'événement pour analyser l'élément de projet en cours de déploiement, et vous pouvez analyser les fichiers à l'emplacement du déploiement en lançant une commande SharePoint définie à cet effet.  
  
     Pour de nombreux types de conflits, vous devrez d'abord déterminer l'étape de déploiement qui est exécutée.  Vous pouvez effectuer cette opération à l'aide de la propriété <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> du paramètre d'arguments d'événement.  Bien qu'il soit généralement raisonnable de détecter les conflits pendant l'étape de déploiement intégrée <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution>, vous pouvez vérifier les conflits au cours de n'importe quelle étape de déploiement.  
  
4.  S'il existe un conflit, utilisez la méthode <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> de la propriété <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> des arguments d'événement pour créer un objet <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>.  Cet objet représente le conflit de déploiement.  Dans l'appel à la méthode <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A>, spécifiez également la méthode qui est appelée pour résoudre le conflit.  
  
## Exemple  
 L'exemple de code suivant illustre le processus de base pour traiter un conflit de déploiement dans une extension d'élément de projet pour les éléments de projet de définition de liste.  Pour traiter un conflit de déploiement pour un autre type d'élément de projet, passez une autre chaîne à <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Pour plus d'informations, consultez [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
 Pour plus de simplicité, le gestionnaire d'événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> dans cet exemple suppose l'existence d'un conflit de déploiement \(autrement dit, il ajoute toujours un nouvel objet <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict>\) et la méthode `Resolve` retourne simplement la valeur **true** pour indiquer que le conflit a été résolu.  Dans un scénario réel, votre gestionnaire d'événements <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> identifie d'abord la présence d'un conflit entre un fichier dans l'élément de projet en cours et un fichier à l'emplacement du déploiement, puis ajoute un objet <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> uniquement si un conflit existe.  Par exemple, vous pouvez utiliser la propriété `e.ProjectItem.Files` dans le gestionnaire d'événements pour analyser les fichiers dans l'élément de projet, et vous pouvez lancer une commande SharePoint pour analyser les fichiers à l'emplacement du déploiement.  De même, dans un scénario réel, la méthode `Resolve` peut appeler une commande SharePoint pour résoudre le conflit sur le site SharePoint.  Pour plus d'informations sur la création de commandes SharePoint, consultez [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/cs/extension/deploymentconflictextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.deploymentconflict/vb/extension/deploymentconflictextension.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Déploiement de l'extension  
 Pour déployer l'extension, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) pour l'assembly et tous les autres fichiers que vous voulez distribuer avec l'extension.  Pour plus d'informations, consultez [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Voir aussi  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  