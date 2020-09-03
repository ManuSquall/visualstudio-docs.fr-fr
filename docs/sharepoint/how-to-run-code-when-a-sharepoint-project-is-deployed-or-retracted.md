---
title: Exécuter du code lors du déploiement ou du retrait d’un projet SharePoint
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bd60c9d7b30d4620630d1f6752bd4c7e8bf1182
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016058"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Comment : exécuter du code lors du déploiement ou du retrait d’un projet SharePoint
  Si vous souhaitez effectuer des tâches supplémentaires lors du déploiement ou du retrait d’un projet SharePoint, vous pouvez gérer les événements déclenchés par Visual Studio. Pour plus d’informations, consultez extension de l' [empaquetage et du déploiement SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Pour exécuter du code lors du déploiement ou du retrait d’un projet SharePoint

1. Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d'informations, voir les rubriques suivantes :

   - [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Dans l’extension, accédez à l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objet. Pour plus d’informations, consultez [Comment : récupérer le service de projet SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Gérez les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> événements et du service de projet.

4. Dans les gestionnaires d’événements, utilisez le <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> paramètre pour obtenir des informations sur la session de déploiement actuelle. Par exemple, vous pouvez déterminer le projet qui se trouve dans la session de déploiement actuelle et s’il est en cours de déploiement ou de retrait.

   L’exemple de code suivant montre comment gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> événements et dans une extension de projet. Cette extension écrit un message supplémentaire dans la fenêtre **sortie** lorsque le déploiement démarre et se termine pour un projet SharePoint.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Comment : exécuter du code lors de l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
