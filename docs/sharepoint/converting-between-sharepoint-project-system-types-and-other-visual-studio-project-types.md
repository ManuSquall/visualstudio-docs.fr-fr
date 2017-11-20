---
title: "Conversion entre Types de système de projet SharePoint et d’autres Types de projet Visual Studio | Documents Microsoft"
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
helpviewer_keywords: SharePoint project service
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 198cb9b2b00b1e09c21ba672999cca557bcd5b48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Conversion entre des types d'un système de projet SharePoint et d'autres types de projets Visual Studio
  Dans certains cas vous pouvez avoir un objet dans le système de projet SharePoint et que vous souhaitez utiliser les fonctionnalités d’un objet correspondant dans le modèle objet automation Visual Studio ou le modèle objet d’intégration, ou vice versa. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode du service de projet SharePoint pour convertir l’objet d’un modèle d’objet différent.  
  
 Par exemple, vous pouvez avoir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet, mais que vous souhaitez utiliser des méthodes qui sont disponibles uniquement sur un <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objet. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode pour convertir le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> à un <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Pour plus d’informations sur le modèle d’objet automation Visual Studio et le modèle objet d’intégration Visual Studio, consultez [vue d’ensemble de la programmation de modèle d’Extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Types de Conversions  
 Le tableau suivant répertorie les types que cette méthode peut convertir entre le système de projet SharePoint et les autres modèles d’objet Visual Studio.  
  
|Type de système de projet SharePoint|Types correspondants dans les modèles objet automation et intégration|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> ou<br /><br /> N’importe quelle interface dans le modèle objet d’intégration Visual Studio qui est implémenté par l’objet COM sous-jacent pour le projet. Ces interfaces incluent <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (ou une interface dérivée), et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Pour obtenir la liste des interfaces principales qui sont implémentées par les projets, consultez [composants principaux du modèle de projet](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> ou<br /><br /> A<xref:System.UInt32> (également appelée VSITEMID) de la valeur qui identifie le membre de projet dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> qui le contient. Cette valeur peut être passée à la *itemid* paramètre de certains <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> méthodes.|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode pour convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> de l’objet à un <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 Cet exemple nécessite :  
  
-   Extension du système de projet SharePoint qui fait référence à l’assembly EnvDTE.dll. Pour plus d’informations, consultez [extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Code qui inscrit le `projectService_ProjectAdded` méthode pour gérer la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> événement d’une <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet. Pour obtenir un exemple, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Comment : récupérer le Service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  