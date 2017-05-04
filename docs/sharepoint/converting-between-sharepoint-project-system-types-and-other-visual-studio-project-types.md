---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  Il arrive, dans certains cas, que l'objet à votre disposition dans le système de projet SharePoint ne soit pas tout à fait satisfaisant et que vous ayez l'intention d'exploiter les fonctionnalités d'un objet correspondant dans le modèle d'objet Automation Visual Studio ou dans le modèle d'objet Intégration, ou vice versa.  Dans de telles situations, vous pouvez utiliser la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> du service de projet SharePoint pour convertir l'objet en un modèle d'objet différent.  
  
 Admettons, par exemple, que vous ayez accès à un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>, mais que vous préfériez utiliser les méthodes applicables uniquement à un objet <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  Dans ce cas, vous pouvez recourir à la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> pour convertir le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en un <xref:EnvDTE.Project> ou un <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Pour plus d'informations sur le modèle d'objet Automation Visual Studio et le modèle d'objet Intégration Visual Studio, consultez [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Types de conversions  
 Le tableau suivant répertorie les types qu'il est possible de convertir, au moyen de cette méthode, entre le système de projet SharePoint et les autres modèles d'objet de Visual Studio.  
  
|Type de système de projet SharePoint|Types correspondants dans les modèles d'objet Automation et Intégration|  
|------------------------------------------|-----------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> ou<br /><br /> Une interface dans le modèle d'objet intégration Visual Studio implémentée par l'objet COM sous\-jacent pour le projet.  Ces interfaces incluent <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(ou une interface dérivée\) et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  Pour obtenir la liste des interfaces principales qui sont implémentées par projets, consultez [Composants de modèle de projet](../extensibility/internals/project-model-core-components.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> ou<br /><br /> Valeur <xref:System.UInt32> \(également appelée VSITEMID\) servant à identifier le membre du projet dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> où il figure.  Cette valeur peut être transmise au paramètre *itemid* de certaines méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser la méthode <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> pour convertir un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 Cet exemple nécessite :  
  
-   une extension du système de projet SharePoint qui comporte une référence à l'assembly EnvDTE.dll.  Pour plus d'informations, consultez [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   du code qui enregistre la méthode `projectService_ProjectAdded` pour gérer l'événement <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  Pour obtenir un exemple, consultez [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Voir aussi  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  