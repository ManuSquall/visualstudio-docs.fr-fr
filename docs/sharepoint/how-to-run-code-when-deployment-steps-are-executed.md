---
title: 'Comment : exécuter du code lorsque des étapes de déploiement sont exécutées | Microsoft Docs'
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
ms.openlocfilehash: b2b0431ab4f985d801a78159fc2d324a29f8b638
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015535"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Comment : exécuter du code lors de l’exécution des étapes de déploiement
  Si vous souhaitez effectuer des tâches supplémentaires pour une étape de déploiement dans un projet SharePoint, vous pouvez gérer les événements déclenchés par les éléments de projet SharePoint avant et après l’exécution de chaque étape de déploiement par Visual Studio. Pour plus d’informations, consultez extension de l' [empaquetage et du déploiement SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Pour exécuter du code lors de l’exécution des étapes de déploiement

1. Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d'informations, voir les rubriques suivantes :

    - [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Dans l’extension, gérez les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> événements et d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objet (dans une extension d’élément de projet ou d’extension de projet) ou un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objet (dans une définition d’un nouveau type d’élément de projet).

3. Dans les gestionnaires d’événements, utilisez les <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> paramètres et pour obtenir des informations sur l’étape de déploiement. Par exemple, vous pouvez déterminer l’étape de déploiement qui s’exécute et si la solution est en cours de déploiement ou de retrait.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment gérer les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> événements et dans une extension de l’élément de projet de l’instance de liste. Cette extension écrit un message supplémentaire dans la fenêtre **sortie** lorsque Visual Studio recycle le pool d’applications pendant le déploiement et le retrait de la solution.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Comment : exécuter du code lors du déploiement ou du retrait d’un projet SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
