---
title: 'Comment : gérer les conflits de déploiement | Microsoft Docs'
description: Consultez un exemple d’implémentation de votre propre code pour gérer les conflits de déploiement pour un élément de projet SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b09db3fecde5d4b87b24963930b2783b0c68052c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213977"
---
# <a name="how-to-handle-deployment-conflicts"></a>Comment : gérer les conflits de déploiement
  Vous pouvez fournir votre propre code pour gérer les conflits de déploiement pour un élément de projet SharePoint. Par exemple, vous pouvez déterminer si des fichiers dans l’élément de projet actuel existent déjà à l’emplacement de déploiement, puis supprimer les fichiers déployés avant le déploiement de l’élément de projet actuel. Pour plus d’informations sur les conflits de déploiement, consultez extension de l' [empaquetage et du déploiement SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Pour gérer un conflit de déploiement

1. Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d'informations, voir les rubriques suivantes :

    - [Comment : créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Comment : créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Comment : définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Dans l’extension, gérez l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> événement d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objet (dans une extension d’élément de projet ou d’extension de projet) ou un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objet (dans une définition d’un nouveau type d’élément de projet).

3. Dans le gestionnaire d’événements, déterminez s’il existe un conflit entre l’élément de projet déployé et la solution déployée sur le site SharePoint, en fonction de critères qui s’appliquent à votre scénario. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> propriété du paramètre d’arguments d’événement pour analyser l’élément de projet déployé, et vous pouvez analyser les fichiers à l’emplacement de déploiement en appelant une commande SharePoint que vous définissez à cet effet.

     Pour de nombreux types de conflits, vous souhaiterez peut-être d’abord déterminer l’étape de déploiement en cours d’exécution. Pour ce faire, vous pouvez utiliser la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> propriété du paramètre d’arguments d’événement. Bien qu’il soit généralement judicieux de détecter les conflits au cours de l' <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> étape de déploiement intégrée, vous pouvez vérifier les conflits au cours d’une étape de déploiement.

4. En cas de conflit, utilisez la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> méthode de la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> propriété des arguments d’événement pour créer un nouvel <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objet. Cet objet représente le conflit de déploiement. Dans votre appel à la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> méthode, spécifiez également la méthode appelée pour résoudre le conflit.

## <a name="example"></a>Exemple
 L’exemple de code suivant illustre le processus de base pour gérer un conflit de déploiement dans une extension d’élément de projet pour les éléments de projet de définition de liste. Pour gérer un conflit de déploiement pour un autre type d’élément de projet, transmettez une chaîne différente à <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Pour plus d’informations, consultez [étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md).

 Par souci de simplicité, le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Gestionnaire d’événements dans cet exemple suppose qu’il existe un conflit de déploiement (autrement dit, il ajoute toujours un nouvel <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objet), et la `Resolve` méthode retourne simplement **true** pour indiquer que le conflit a été résolu. Dans un scénario réel, votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Gestionnaire d’événements détermine d’abord s’il existe un conflit entre un fichier dans l’élément de projet actif et un fichier à l’emplacement de déploiement, puis ajoute un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objet uniquement en cas de conflit. Par exemple, vous pouvez utiliser la `e.ProjectItem.Files` propriété dans le gestionnaire d’événements pour analyser les fichiers dans l’élément de projet, et vous pouvez appeler une commande SharePoint pour analyser les fichiers à l’emplacement de déploiement. De même, dans un scénario réel, la `Resolve` méthode peut appeler une commande SharePoint pour résoudre le conflit sur le site SharePoint. Pour plus d’informations sur la création de commandes SharePoint, consultez [procédure : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compiler le code
 Cet exemple nécessite des références aux assemblys suivants :

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Déployer l’extension
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Voir aussi
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Étendre les éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Comment : exécuter du code lors de l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Comment : créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
