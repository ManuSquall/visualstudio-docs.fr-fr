---
title: 'Comment : récupérer le service de projet SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f49883337c5748c0f8bcab5d0a88e02612e51b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015551"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Comment : récupérer le service de projet SharePoint
  Vous pouvez accéder au service de projet SharePoint dans les types de solutions suivants :

- Extension du système de projet SharePoint, telle qu’une extension de projet, une extension d’élément de projet ou une définition de type d’élément de projet. Pour plus d’informations sur ces types d’extensions, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Extension du nœud **Connexions SharePoint** dans **Explorateur de serveurs**. Pour plus d’informations sur ces types d’extensions, consultez [étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Autre type d’extension Visual Studio, tel qu’un VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Récupérer le service dans les extensions système de projet
 Dans toute extension du système de projet SharePoint, vous pouvez accéder au service de projet à l’aide <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> de la propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet.

 Vous pouvez également récupérer le service de projet à l’aide des procédures suivantes.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Pour récupérer le service dans une extension de projet

1. Dans votre implémentation de l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface, localisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> méthode.

2. Utilisez le paramètre *ProjectService* pour accéder au service.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message dans la fenêtre **sortie** et **liste d’erreurs** fenêtre dans une extension de projet simple.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Pour plus d’informations sur la création d’extensions de projet, consultez [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Pour récupérer le service dans une extension d’élément de projet

1. Dans votre implémentation de l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface, localisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> méthode.

2. Utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> propriété du paramètre *projectItemType* pour récupérer le service.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message dans la fenêtre **sortie** et **liste d’erreurs** fenêtre dans une extension simple de l’élément de projet **définition de liste** .

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Pour plus d’informations sur la création d’extensions d’élément de projet, consultez [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Pour récupérer le service dans une définition de type d’élément de projet

1. Dans votre implémentation de l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface, localisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode.

2. Utilisez la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> propriété du paramètre *TypeDefinition* pour récupérer le service.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message dans la fenêtre **sortie** et **liste d’erreurs** fenêtre dans une définition de type d’élément de projet simple.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Pour plus d’informations sur la définition des types d’éléments de projet, consultez [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Récupérer le service dans les extensions de Explorateur de serveurs
 Dans une extension du nœud **Connexions SharePoint** dans **Explorateur de serveurs**, vous pouvez accéder au service de projet à l’aide <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> de la propriété d’un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Pour récupérer le service dans une extension de Explorateur de serveurs

1. Récupérez un <xref:System.IServiceProvider> objet à partir de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet dans votre extension.

2. Utilisez la <xref:System.IServiceProvider.GetService%2A> méthode pour demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message dans la fenêtre **sortie** et **liste d’erreurs** fenêtre à partir d’un menu contextuel que l’extension ajoute à la liste des nœuds dans **Explorateur de serveurs**.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Pour plus d’informations sur l’extension du nœud **Connexions SharePoint** dans **Explorateur de serveurs**, consultez [Comment : étendre un nœud SharePoint dans Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Récupérer le service dans d’autres extensions Visual Studio
 Vous pouvez récupérer le service de projet dans un VSPackage, ou dans n’importe quelle extension Visual Studio qui a accès à un <xref:EnvDTE80.DTE2> objet dans le modèle objet Automation, tel qu’un Assistant modèle de projet qui implémente l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.

 Dans un VSPackage, vous pouvez demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet à l’aide de l’une des méthodes suivantes :

- <xref:System.IServiceProvider.GetService%2A>Méthode d’un VSPackage managé qui dérive de la <xref:Microsoft.VisualStudio.Shell.Package> classe. Pour plus d’informations, consultez [Comment : obtenir un service](../extensibility/how-to-get-a-service.md).

- Méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> . Pour plus d’informations, consultez [utiliser GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  Dans une extension Visual Studio qui a accès à un <xref:EnvDTE80.DTE2> objet, vous pouvez demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet à l’aide <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> de la méthode d’un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objet. Pour plus d’informations, consultez [obtention d’un service à partir de l’objet DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Voir aussi
- [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Comment : obtenir un service](../extensibility/how-to-get-a-service.md)
- [Comment : utiliser des assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
