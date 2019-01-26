---
title: 'Procédure : Gérer les conflits de déploiement | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd28e7a9f0fc04a704d6d3600fb80390d9509de1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863043"
---
# <a name="how-to-handle-deployment-conflicts"></a>Procédure : Gérer les conflits de déploiement
  Vous pouvez fournir votre propre code pour gérer les conflits de déploiement pour un élément de projet SharePoint. Par exemple, vous pouvez déterminer si tous les fichiers dans l’élément de projet en cours existent déjà dans l’emplacement de déploiement, puis supprimez les fichiers déployés avant le déploiement de l’élément de projet actuel. Pour plus d’informations sur les conflits de déploiement, consultez [extension SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Pour gérer un conflit de déploiement  
  
1.  Créer une extension d’élément de projet, une extension de projet ou une définition d’un nouveau type d’élément de projet. Pour plus d’informations, consultez les rubriques suivantes :  
  
    -   [Guide pratique pour Créer une extension d’élément de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Guide pratique pour Créer une extension de projet SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Guide pratique pour Définir un type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Dans l’extension, gérez les <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> événement d’un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objet (dans une extension d’élément de projet ou une extension de projet) ou un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objet (dans une définition d’un nouveau type d’élément de projet).  
  
3.  Dans le Gestionnaire d’événements, déterminez s’il existe un conflit entre l’élément de projet est en cours de déploiement et la solution déployée sur le site SharePoint, en fonction de critères qui s’appliquent à votre scénario. Vous pouvez utiliser le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> propriété l’arguments du paramètre d’événement pour analyser l’élément de projet est déployé et vous pouvez analyser les fichiers à l’emplacement de déploiement en appelant une commande SharePoint que vous définissez à cet effet.  
  
     Pour de nombreux types de conflits, vous pouvez tout d’abord également déterminer étape de déploiement qui s’exécute. Vous pouvez le faire à l’aide de la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> propriété l’arguments du paramètre d’événement. Bien qu’il est généralement judicieux de détecter les conflits pendant l’intégrée <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> étape de déploiement, vous pouvez vérifier les conflits au cours de des étapes de déploiement.  
  
4.  Si un conflit existe, utilisez le <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> méthode de la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> propriété des arguments d’événement pour créer un nouveau <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objet. Cet objet représente le conflit de déploiement. Dans votre appel à la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> (méthode), spécifiez également la méthode est appelée pour résoudre le conflit.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre le processus de base pour la gestion d’un conflit de déploiement dans une extension d’élément de projet pour les éléments de projet de définition de liste. Pour gérer un conflit de déploiement pour un autre type d’élément de projet, passez une chaîne différente pour le <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Pour plus d’informations, consultez [éléments de projet SharePoint étendre](../sharepoint/extending-sharepoint-project-items.md).  
  
 Par souci de simplicité, le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Gestionnaire d’événements dans cet exemple suppose qu’il existe un conflit de déploiement (autrement dit, il ajoute toujours un nouveau <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objet) et le `Resolve` méthode renvoie simplement **true** pour indiquer que le conflit a été résolu. Dans un scénario réel, votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Gestionnaire d’événements est tout d’abord déterminer si un conflit existe entre un fichier dans l’élément de projet en cours et un fichier à l’emplacement de déploiement, puis ajoutez un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> uniquement l’objet si un conflit existe. Par exemple, vous pouvez utiliser le `e.ProjectItem.Files` propriété dans le Gestionnaire d’événements pour analyser les fichiers dans l’élément de projet et que vous pouvez appeler une commande SharePoint pour analyser les fichiers à l’emplacement de déploiement. De même, dans un scénario réel le `Resolve` méthode peut appeler une commande SharePoint pour résoudre le conflit sur le site SharePoint. Pour plus d’informations sur la création de commandes SharePoint, consultez [Comment : Créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple nécessite des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Déployer l’extension  
 Pour déployer l’extension, créez un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Pour plus d’informations, consultez [déployer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi
 [Étendre le déploiement et empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Étendre des éléments de projet SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Guide pratique pour Exécuter du code quand l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Guide pratique pour Créer une commande SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
