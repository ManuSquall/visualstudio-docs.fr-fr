---
title: 'Procédure : Récupérer le Service de projet SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 75caa29d90b41dc696ce586d50928b2adb0875f9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067519"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Procédure : Récupérer le service de projet SharePoint
  Le service de projet SharePoint dans les types suivants de solutions est accessible :

- Une extension du système de projet SharePoint, comme une extension de projet, une extension d’élément de projet ou une définition de type élément de projet. Pour plus d’informations sur ces types d’extensions, consultez [étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Une extension de la **connexions SharePoint** nœud **Explorateur de serveurs**. Pour plus d’informations sur ces types d’extensions, consultez [étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Un autre type d’extension de Visual Studio, par exemple un VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Récupérer le service dans les extensions de système de projet
 Dans toute extension du système de projet SharePoint, vous pouvez accéder au service de projet à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objet.

 Vous pouvez également récupérer le service de projet en utilisant les procédures suivantes.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Pour récupérer le service dans une extension de projet

1. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface, recherchez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> (méthode).

2. Utilisez le *projectService* paramètre pour accéder au service.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre dans une extension de projet simple.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Pour plus d’informations sur la création d’extensions de projet, consultez [Comment : Créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Pour récupérer le service dans une extension d’élément de projet

1. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface, recherchez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> (méthode).

2. Utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> propriété de la *projectItemType* paramètre à récupérer le service.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre dans une extension simple du **définition de liste** élément de projet.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Pour plus d’informations sur la création d’extensions d’élément de projet, consultez [Comment : Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Pour récupérer le service dans la définition de type d’un élément de projet

1. Dans votre implémentation de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface, recherchez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (méthode).

2. Utilisez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> propriété de la *typeDefinition* paramètre à récupérer le service.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre dans une définition de type de projet simple élément.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Pour plus d’informations sur la définition des types d’éléments de projet, consultez [Comment : Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Récupérer le service dans les extensions de l’Explorateur de serveurs
 Dans une extension de la **connexions SharePoint** nœud dans **Explorateur de serveurs**, vous pouvez accéder au service de projet à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Pour récupérer le service dans une extension de l’Explorateur de serveurs

1. Obtenir un <xref:System.IServiceProvider> à partir de l’objet le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propriété d’un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objet dans votre extension.

2. Utilisez le <xref:System.IServiceProvider.GetService%2A> méthode pour demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet.

     L’exemple de code suivant montre comment utiliser le service de projet pour écrire un message à la **sortie** fenêtre et **liste d’erreurs** fenêtre à partir d’un menu contextuel que l’extension ajoute aux nœuds de liste dans **Explorateur de serveurs**.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Pour plus d’informations sur l’extension de la **connexions SharePoint** nœud **Explorateur de serveurs**, consultez [Comment : Étendre un nœud SharePoint dans l’Explorateur de serveurs](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Récupérer le Service dans les autres extensions Visual Studio
 Vous pouvez récupérer le service de projet dans un VSPackage, ou dans n’importe quelle extension de Visual Studio qui a accès à un <xref:EnvDTE80.DTE2> objet dans le modèle objet automation, telles qu’un Assistant de modèle de projet qui implémente le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.

 Dans un VSPackage, vous pouvez demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet en utilisant l’une des méthodes suivantes :

- Le <xref:System.IServiceProvider.GetService%2A> méthode d’un VSPackage managé qui dérive de la <xref:Microsoft.VisualStudio.Shell.Package> classe. Pour plus d'informations, voir [Procédure : Obtenir un Service](../extensibility/how-to-get-a-service.md).

- La méthode statique <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (méthode). Pour plus d’informations, consultez [utiliser GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  Dans une extension Visual Studio qui a accès à un <xref:EnvDTE80.DTE2> objet, vous pouvez demander un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet à l’aide de la <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> méthode d’un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objet. Pour plus d’informations, consultez [l’obtention d’un service à partir de l’objet DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Voir aussi
- [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Guide pratique pour Bénéficiez d’un service](../extensibility/how-to-get-a-service.md)
- [Guide pratique pour Utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
