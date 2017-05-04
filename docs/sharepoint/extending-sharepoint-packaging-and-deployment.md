---
title: "Extending SharePoint Packaging and Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4789ebb2-12bc-42b9-9427-e63d77137765
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Packaging and Deployment
  Vous pouvez étendre le processus d'empaquetage et de déploiement pour les projets SharePoint.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="creating_deployment_steps"></a> Création des étapes de déploiement  
 Quand vous déployez un projet SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] exécute une série d'étapes de déploiement.  Visual Studio offre des étapes de déploiement intégrées pour de nombreuses tâches \(retrait et ajout de solutions, par exemple\).  Mais rien ne vous empêche de créer vos propres étapes de déploiement.  
  
 Pour apprendre à créer progressivement une étape de déploiement, consultez [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="creating_deployment_configurations"></a> Création de configurations de déploiement  
 Une configuration de déploiement est un ensemble d'étapes de déploiement exécutées pour un projet donné, mais qui peuvent affecter tous les éléments de projet SharePoint.  Chaque configuration de déploiement inclut un ensemble d'étapes exécutées quand le projet est déployé, et un autre ensemble exécuté quand le projet est retiré.  [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] inclut deux configurations de déploiement intégrées, mais rien ne vous empêche de créer vos propres configurations.  Quand vous créez une configuration de déploiement, vous pouvez y inclure les étapes de déploiement intégrées et vos propres étapes de déploiement.  
  
 Pour apprendre à créer une configuration de déploiement, étape par étape, consultez [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
##  <a name="run_code_before_and_after_each_deployment_step"></a> Exécution de code pendant le déploiement ou le retrait d'une solution SharePoint  
 Vous pouvez gérer des événements pour exécuter des tâches supplémentaires quand une solution SharePoint est déployée ou retirée.  Visual Studio déclenche des événements que vous pouvez gérer dans les scénarios suivants :  
  
-   Avant et après l'exécution de chaque étape de déploiement pour un élément de projet SharePoint.  Pour plus d'informations, consultez [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Avant et après le déploiement ou le retrait d'un projet SharePoint.  Pour plus d'informations, consultez [How to: Run Code When a SharePoint Project is Deployed or Retracted](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
##  <a name="deployment_conflicts"></a> Gestion des conflits de déploiement  
 Certains types d'éléments de projet SharePoint, notamment les modules, les composants WebPart, les instances de listes et les types de contenu, fournissent une résolution intégrée des conflits de déploiement.  Quand vous déployez une solution qui contient un de ces éléments de projet, Visual Studio vérifie d'abord si un fichier existe déjà sur le site SharePoint avec le même nom, URL ou ID qu'un fichier dans l'élément que vous déployez.  Si un conflit est identifié, Visual Studio peut le résoudre automatiquement, ou il peut vous laisser décider si vous souhaitez une prise en charge de la résolution du conflit par Visual Studio ou l'annulation du déploiement.  Pour plus d'informations, consultez [Dépannage de la création de packages et du déploiement SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Vous pouvez étendre cette fonctionnalité en fournissant votre propre code qui vérifie et résout les conflits de déploiement.  Pour plus d'informations, consultez [How to: Handle Deployment Conflicts](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
##  <a name="run_command_line_operations_before_or_after_a_project_is_deployed"></a> Exécution des opérations de ligne de commande avant ou après le déploiement d'un projet  
 Si vous souhaitez exécuter une opération de ligne de commande pendant le déploiement d'une solution SharePoint, vous pouvez définir les propriétés <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> et <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> d'un objet <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  Visual Studio exécute ces commandes avant et après le déploiement du projet.  
  
 Dans certains cas, vous pouvez rencontrer des conflits de déploiement.  Vous pouvez résoudre les conflits de plusieurs manières.  Pour plus d'informations, consultez [Dépannage de la création de packages et du déploiement SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
##  <a name="customizing_validation_rules"></a> Personnalisation des règles de validation  
 Avant de déployer un package de solution \(.wsp\), vous pouvez créer des règles de validation de fonctionnalité et de package personnalisées pour vérifier que la fonctionnalité ou le package est valide.  Par exemple, vous pouvez signaler des informations, des avertissements ou des erreurs aux développeurs pour les aider à résoudre les problèmes de validation.  Pour plus d'informations, consultez [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## Voir aussi  
 [How to: Run Code When Deployment Steps are Executed](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  