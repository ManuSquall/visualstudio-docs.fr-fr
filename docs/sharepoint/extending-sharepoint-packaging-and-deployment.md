---
title: "Extension SharePoint empaquetage et déploiement | Documents Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b88c89d9464b5ac9bc588c4364de97c1f4e281d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="extending-sharepoint-packaging-and-deployment"></a>Extension de la création de packages et du déploiement SharePoint
  Vous pouvez étendre le processus d'empaquetage et de déploiement pour les projets SharePoint.
  
##  <a name="creating-deployment-steps"></a>Création des étapes de déploiement  
 Quand vous déployez un projet SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] exécute une série d'étapes de déploiement. Visual Studio offre des étapes de déploiement intégrées pour de nombreuses tâches (retrait et ajout de solutions, par exemple). Mais rien ne vous empêche de créer vos propres étapes de déploiement.  
  
 Pour une procédure pas à pas qui montre comment créer une étape de déploiement, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating-deployment-configurations"></a>Création de configurations de déploiement  
 Une configuration de déploiement est un ensemble d'étapes de déploiement exécutées pour un projet donné, mais qui peuvent affecter tous les éléments de projet SharePoint. Chaque configuration de déploiement inclut un ensemble d'étapes exécutées quand le projet est déployé, et un autre ensemble exécuté quand le projet est retiré. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)]inclut deux configurations de déploiement intégrées, mais vous pouvez également créer vos propres. Quand vous créez une configuration de déploiement, vous pouvez y inclure les étapes de déploiement intégrées et vos propres étapes de déploiement.  
  
 Pour une procédure pas à pas qui montre comment créer une configuration de déploiement, consultez [procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Exécution de code pendant le déploiement ou le retrait d'une solution SharePoint  
 Vous pouvez gérer des événements pour exécuter des tâches supplémentaires quand une solution SharePoint est déployée ou retirée. Visual Studio déclenche des événements que vous pouvez gérer dans les scénarios suivants :  
  
-   Avant et après l'exécution de chaque étape de déploiement pour un élément de projet SharePoint. Pour plus d’informations, consultez [Comment : exécuter Code lors des étapes de déploiement sont exécutées](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Avant et après le déploiement ou le retrait d'un projet SharePoint. Pour plus d’informations, consultez [Comment : exécuter Code lorsqu’un projet SharePoint est déployé ou le retrait](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="handling-deployment-conflicts"></a>Gestion des conflits de déploiement  
 Certains types d'éléments de projet SharePoint, notamment les modules, les composants WebPart, les instances de listes et les types de contenu, fournissent une résolution intégrée des conflits de déploiement. Quand vous déployez une solution qui contient un de ces éléments de projet, Visual Studio vérifie d'abord si un fichier existe déjà sur le site SharePoint avec le même nom, URL ou ID qu'un fichier dans l'élément que vous déployez. Si un conflit est identifié, Visual Studio peut le résoudre automatiquement, ou il peut vous laisser décider si vous souhaitez une prise en charge de la résolution du conflit par Visual Studio ou l'annulation du déploiement. Pour plus d’informations, consultez [résolution des problèmes de conditionnement de SharePoint et de déploiement](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Vous pouvez étendre cette fonctionnalité en fournissant votre propre code qui vérifie et résout les conflits de déploiement. Pour plus d’informations, consultez [Comment : gérer les conflits de déploiement](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Exécution des opérations de ligne de commande avant ou après le déploiement d'un projet  
 Si vous souhaitez exécuter une opération de ligne de commande pendant le déploiement d'une solution SharePoint, vous pouvez définir les propriétés <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio exécute ces commandes avant et après le déploiement du projet.  
  
 Dans certains cas, vous pouvez rencontrer des conflits de déploiement. Vous pouvez résoudre les conflits de plusieurs manières. Pour plus d’informations, consultez [résolution des problèmes de conditionnement de SharePoint et de déploiement](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing-validation-rules"></a>Personnalisation des règles de validation  
 Avant de déployer un package de solution (.wsp), vous pouvez créer des règles de validation de fonctionnalité et de package personnalisées pour vérifier que la fonctionnalité ou le package est valide. Par exemple, vous pouvez signaler des informations, des avertissements ou des erreurs aux développeurs pour les aider à résoudre les problèmes de validation. Pour plus d’informations, consultez [Comment : créer des fonctionnalités personnalisées et les règles de Validation de Package pour les Solutions SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : exécuter Code lors des étapes de déploiement sont exécutées.](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Procédure pas à pas : Création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Comment : créer des règles de Validation de Package et de fonctionnalité personnalisée pour les Solutions SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
