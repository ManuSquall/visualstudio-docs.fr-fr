---
title: "Comment : récupérer le Service de projet SharePoint | Documents Microsoft"
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
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5ecc739da7cc3aa78a5c175ae323f5cd2447d40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Comment : récupérer le service de projet SharePoint
  Vous pouvez accéder au service de projet SharePoint dans les types suivants de solutions :  
  
-   Extension du système de projet SharePoint, comme une extension de projet, une extension d’élément de projet ou une définition de type élément de projet. Pour plus d’informations sur ces types d’extensions, consultez [extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Une extension de la **connexions SharePoint** nœud **l’Explorateur de serveurs**. Pour plus d’informations sur ces types d’extensions, consultez [extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Un autre type d’extension de Visual Studio, par exemple un VSPackage.  
  
## <a name="retrieving-the-service-in-project-system-extensions"></a>Extraction du Service dans les Extensions de système de projet  
 Dans les extensions du système de projet SharePoint, vous pouvez accéder au service du projet à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet.  
  
 Vous pouvez également récupérer le service de projet à l’aide des procédures suivantes.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Pour extraire le service dans une extension de projet  
  
1.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> de l’interface, recherchez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> (méthode).  
  
2.  Utilisez le *projectService* paramètre pour accéder au service.  
  
     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre dans une extension de projet simple.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Pour plus d’informations sur la création d’extensions de projet, consultez [Comment : créer une Extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Pour extraire le service dans une extension d’élément de projet  
  
1.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> de l’interface, recherchez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> (méthode).  
  
2.  Utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> propriété de la *projectItemType* paramètre à récupérer le service.  
  
     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre dans une extension simple de la **la définition de liste** élément de projet.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Pour plus d’informations sur la création d’extensions d’élément de projet, consultez [Comment : créer une Extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Pour extraire le service dans une définition de type d’élément projet  
  
1.  Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> de l’interface, recherchez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (méthode).  
  
2.  Utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> propriété de la *typeDefinition* paramètre à récupérer le service.  
  
     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre dans une définition de type de projet simple élément.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Pour plus d’informations sur la définition des types d’éléments de projet, consultez [Comment : définir un Type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieving-the-service-in-server-explorer-extensions"></a>Extraction du Service dans les Extensions de l’Explorateur de serveur  
 Dans une extension de la **connexions SharePoint** nœud dans **l’Explorateur de serveurs**, vous pouvez accéder au service de projet à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Pour extraire le service dans une extension de l’Explorateur de serveurs  
  
1.  Obtenir un <xref:System.IServiceProvider> à partir de l’objet le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> l’objet dans votre extension.  
  
2.  Utilisez le <xref:System.IServiceProvider.GetService%2A> méthode pour demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet.  
  
     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre à partir d’un menu contextuel que l’extension ajoute aux nœuds de liste dans **L’Explorateur de serveurs**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Pour plus d’informations sur l’extension de la **connexions SharePoint** nœud **l’Explorateur de serveurs**, consultez [Comment : étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieving-the-service-in-other-visual-studio-extensions"></a>Extraction du Service dans les autres Extensions de Visual Studio  
 Vous pouvez récupérer le service de projet dans un VSPackage ou dans toute extension Visual Studio qui a accès à un <xref:EnvDTE80.DTE2> objet dans le modèle objet automation, telles qu’un Assistant de modèle de projet qui implémente le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
 Dans un VSPackage, vous pouvez demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet en utilisant l’une des méthodes suivantes :  
  
-   Le <xref:System.IServiceProvider.GetService%2A> méthode d’un VSPackage managé qui dérive de la <xref:Microsoft.VisualStudio.Shell.Package> classe. Pour plus d’informations, consultez [Comment : obtenir un Service](../extensibility/how-to-get-a-service.md).  
  
-   La méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (méthode). Pour plus d’informations, consultez [GetGlobalService d’utilisation](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
 Dans une extension Visual Studio qui a accès à un <xref:EnvDTE80.DTE2> objet, vous pouvez demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet à l’aide de la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode d’un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objet. Pour plus d’informations, consultez [mise en route d’un service à partir de l’objet DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Comment : obtenir un Service](../extensibility/how-to-get-a-service.md)   
 [Guide pratique pour utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  