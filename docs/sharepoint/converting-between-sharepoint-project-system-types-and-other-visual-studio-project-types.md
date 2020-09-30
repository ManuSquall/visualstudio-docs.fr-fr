---
title: 'Convertir : types de système de projet SharePoint vers/à partir d’autres types'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44b3e32114b10eae776f39e4c3d7337bba636f3f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584644"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Effectuer une conversion entre des types système de projet SharePoint et d’autres types de projets Visual Studio
  Dans certains cas, vous pouvez avoir un objet dans le système de projet SharePoint et vous souhaitez utiliser les fonctionnalités d’un objet correspondant dans le modèle objet Automation Visual Studio ou le modèle objet d’intégration, ou vice versa. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode du service de projet SharePoint pour convertir l’objet en un modèle d’objet différent.

 Par exemple, vous pouvez avoir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet, mais vous souhaitez utiliser des méthodes qui sont uniquement disponibles sur un <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objet ou. Dans ce cas, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode pour convertir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Pour plus d’informations sur le modèle objet Automation Visual Studio et le modèle objet d’intégration Visual Studio, consultez [vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Types de conversions
 Le tableau suivant répertorie les types que cette méthode peut convertir entre le système de projet SharePoint et les autres modèles d’objet Visual Studio.

|Type de système de projet SharePoint|Types correspondants dans les modèles objet Automation et intégration|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> ou<br /><br /> Toute interface dans le modèle objet d’intégration Visual Studio qui est implémentée par l’objet COM sous-jacent pour le projet. Ces interfaces incluent <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (ou une interface dérivée) et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Pour obtenir la liste des interfaces principales implémentées par les projets, consultez [composants de base du modèle de projet](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> ou<br /><br /> <xref:System.UInt32>Valeur (également appelée VSITEMID) qui identifie le membre du projet dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> qui le contient. Cette valeur peut être passée au paramètre *ItemId* de certaines <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> méthodes.|

## <a name="example"></a> Exemple
 L’exemple de code suivant montre comment utiliser la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> méthode pour convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet en <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Cet exemple nécessite :

- Extension du système de projet SharePoint qui a une référence à l’assembly de *EnvDTE.dll* . Pour plus d’informations, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Code qui inscrit la `projectService_ProjectAdded` méthode pour gérer l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> événement d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet. Pour obtenir un exemple, consultez Guide pratique [pour créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Voir aussi

- [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Comment : récupérer le service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Vue d’ensemble du modèle de programmation des extensions d’outils SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
