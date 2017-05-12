---
title: "Using the SharePoint Project Service"
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
  - "SharePoint project service"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Using the SharePoint Project Service
  Le système de projet SharePoint inclut un service de projet que vous pouvez utiliser pour effectuer des tâches liées au système de projet.  Le service de projet est un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
 Vous pouvez accéder au service de projet SharePoint dans toute extension d'outils SharePoint.  Vous pouvez également y accéder dans d'autres types d'extensions Visual Studio, comme les modules complémentaires et VSPackages.  Pour plus d'informations, voir [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## Fonctionnalités du service de projet  
 Le tableau suivant répertorie les tâches que vous pouvez effectuer à l'aide du service de projet SharePoint et la méthode ou propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> à utiliser pour effectuer chaque tâche.  
  
|Tâche|Membre à utiliser|  
|-----------|-----------------------|  
|Accéder à un projet SharePoint ouvert dans Visual Studio.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|  
|Accéder à tous les types d'éléments de projet SharePoint disponibles \(y compris les types d'éléments de projet intégrés et personnalisés\).|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|  
|Accéder à toutes les étapes de déploiement disponibles pour les projets SharePoint \(y compris les étapes de déploiement intégrées et personnalisées\).|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|  
|Accéder aux événements qui sont déclenchés quand un développeur refactorise le code dans un projet SharePoint.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|  
|Exécuter une *commande SharePoint* personnalisée qui appelle le modèle d'objet serveur SharePoint.  Pour plus d'informations sur les commandes SharePoint, voir [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|  
|Convertir un type dans le système de projet SharePoint en un type dans le modèle d'objet automation Visual Studio ou le modèle d'objet d'intégration, et vice versa.  Pour plus d'informations, voir [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Écrire des messages dans la fenêtre **Sortie** ou **Liste d'erreurs** dans Visual Studio.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|  
|Accéder aux autres services qui sont disponibles dans Visual Studio.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|  
|Récupérer le chemin d'accès au dossier d'installation du site SharePoint local qui est utilisé pour le débogage de la solution.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|  
|Déterminer si [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ou [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] est installé sur l'ordinateur.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|  
|Valider une fonctionnalité ou un package dans une solution SharePoint.|Propriété <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|  
  
## Voir aussi  
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Comment : obtenir un service à partir de l'objet DTE](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  