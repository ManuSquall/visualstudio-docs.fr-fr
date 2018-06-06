---
title: Conversion entre Types de système de projet SharePoint et d’autres Types de projet Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64de38fe796ce3c1e0d333a22582ad2973e1c4d2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765357"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Effectuer une conversion entre des types de système de projet SharePoint et d’autres types de projet Visual Studio
  Dans certains cas vous pouvez avoir un objet dans le système de projet SharePoint et que vous souhaitez utiliser les fonctionnalités d’un objet correspondant dans le modèle objet automation Visual Studio ou le modèle objet d’intégration, ou vice versa. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode du service de projet SharePoint pour convertir l’objet d’un modèle d’objet différent.  
  
 Par exemple, vous pouvez avoir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet, mais que vous souhaitez utiliser des méthodes qui sont disponibles uniquement sur un <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objet. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode pour convertir le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> à un <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Pour plus d’informations sur le modèle d’objet automation Visual Studio et le modèle objet d’intégration Visual Studio, consultez [vue d’ensemble de la programmation de modèle d’Extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Types de conversions
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
  
-   Une extension du système de projet SharePoint qui possède une référence à la *EnvDTE.dll* assembly. Pour plus d’informations, consultez [extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Code qui inscrit le `projectService_ProjectAdded` méthode pour gérer la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> événement d’une <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet. Pour obtenir un exemple, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Voir aussi
 [L’utilisation du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Comment : récupérer le Service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
