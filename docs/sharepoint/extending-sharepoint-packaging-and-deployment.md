---
title: Extension de SharePoint Packaging and Deployment | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c6ca4b347cdd733ac166782d8e78dc8e78e0772
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325363"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Étendre le déploiement et empaquetage de SharePoint
  Vous pouvez étendre le processus d'empaquetage et de déploiement pour les projets SharePoint.
  
## <a name="create-deployment-steps"></a>Créer des étapes de déploiement
 Quand vous déployez un projet SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] exécute une série d'étapes de déploiement. Visual Studio offre des étapes de déploiement intégrées pour de nombreuses tâches (retrait et ajout de solutions, par exemple). Mais rien ne vous empêche de créer vos propres étapes de déploiement.  
  
 Pour une procédure pas à pas qui montre comment créer une étape de déploiement, consultez [procédure pas à pas : créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="create-deployment-configurations"></a>Créer des configurations de déploiement
 Une configuration de déploiement est un ensemble d'étapes de déploiement exécutées pour un projet donné, mais qui peuvent affecter tous les éléments de projet SharePoint. Chaque configuration de déploiement inclut un ensemble d'étapes exécutées quand le projet est déployé, et un autre ensemble exécuté quand le projet est retiré. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] comprend deux configurations de déploiement intégrées, mais vous pouvez également créer vos propres. Quand vous créez une configuration de déploiement, vous pouvez y inclure les étapes de déploiement intégrées et vos propres étapes de déploiement.  
  
 Pour une procédure pas à pas qui montre comment créer une configuration de déploiement, consultez [procédure pas à pas : créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Exécuter du code quand une solution SharePoint est déployée ou retirée
 Vous pouvez gérer des événements pour exécuter des tâches supplémentaires quand une solution SharePoint est déployée ou retirée. Visual Studio déclenche des événements que vous pouvez gérer dans les scénarios suivants :  
  
-   Avant et après l'exécution de chaque étape de déploiement pour un élément de projet SharePoint. Pour plus d’informations, consultez [Comment : exécuter du code quand l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Avant et après le déploiement ou le retrait d'un projet SharePoint. Pour plus d’informations, consultez [Comment : exécuter du code quand un projet SharePoint est déployé ou retiré](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
## <a name="handle-deployment-conflicts"></a>Gérer les conflits de déploiement
 Certains types d’éléments de projet SharePoint, notamment les modules, les composants WebPart, les instances de listes et les types de contenu, fournissent une résolution intégrée des conflits de déploiement. Quand vous déployez une solution qui contient un de ces éléments de projet, Visual Studio vérifie d'abord si un fichier existe déjà sur le site SharePoint avec le même nom, URL ou ID qu'un fichier dans l'élément que vous déployez. Si un conflit est identifié, Visual Studio peut le résoudre automatiquement, ou il peut vous laisser décider si vous souhaitez une prise en charge de la résolution du conflit par Visual Studio ou l'annulation du déploiement. Pour plus d’informations, consultez [Troubleshooting SharePoint Packaging et déploiement](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Vous pouvez étendre cette fonctionnalité en fournissant votre propre code qui vérifie et résout les conflits de déploiement. Pour plus d’informations, consultez [Comment : gérer les conflits de déploiement](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Exécuter des opérations de ligne de commande avant ou après qu’un projet est déployé.
 Si vous souhaitez exécuter une opération de ligne de commande pendant le déploiement d'une solution SharePoint, vous pouvez définir les propriétés <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio exécute ces commandes avant et après le déploiement du projet.  
  
 Dans certains cas, vous pouvez rencontrer des conflits de déploiement. Vous pouvez résoudre les conflits de plusieurs manières. Pour plus d’informations, consultez [empaquetage de résoudre les problèmes de SharePoint et de déploiement](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="customize-validation-rules"></a>Personnaliser les règles de validation
 Avant de déployer un package de solution (.wsp), vous pouvez créer des règles de validation de fonctionnalité et de package personnalisées pour vérifier que la fonctionnalité ou le package est valide. Par exemple, vous pouvez signaler des informations, des avertissements ou des erreurs aux développeurs pour les aider à résoudre les problèmes de validation. Pour plus d’informations, consultez [Comment : créer des règles de validation pour les solutions SharePoint fonctionnalité personnalisée et un package](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Voir aussi
 [Comment : exécuter du code quand l’exécution des étapes de déploiement](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Comment : créer des règles de validation pour les solutions SharePoint fonctionnalité personnalisée et un package](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
