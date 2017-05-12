---
title: "Extending the SharePoint Project System"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  Vous pouvez créer des solutions SharePoint à l'aide d'un jeu de modèles de projet et de modèles d'élément dans Visual Studio.  Ces modèles sont conformes aux spécifications de nombreux scénarios de développement, mais vous pouvez découvrir certains cas où il n'offrent pas toutes les fonctionnalités dont vous avez besoin.  Dans ce cas, vous pouvez envisager une extension du système de projet SharePoint.  
  
## Vue d'ensemble du système de projet SharePoint  
 Le système de projet SharePoint repose sur un composant fondamental : les *éléments de projet SharePoint*.  Un élément de projet SharePoint représente une personnalisation SharePoint unique, telle qu'une définition de liste, un composant WebPart ou un type de contenu.  
  
 Un projet SharePoint est un projet Visual Studio qui inclut un ou plusieurs éléments de projet SharePoint.  Les projets SharePoint contiennent également des composant additionnels qui définissent le regroupement des éléments de projet en fonctionnalités et packages en vue de leur déploiement.  
  
 Pour plus d'informations sur le contenu des éléments de projet SharePoint et des projets SharePoint, consultez [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Comment : étendre le système de projet SharePoint  
 Voici les différentes manières de procéder :  
  
-   Définissez vos propres types d'éléments de projet SharePoint et associez\-les à de nouveaux modèles d'élément ou modèles de projet dans Visual Studio.  Par exemple, vous pouvez définir un type d'élément de projet SharePoint pour la création d'une action personnalisée ou d'un champ.  Pour plus d’informations, consultez [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Étendez les types d'éléments de projet SharePoint qui sont déjà installés dans Visual Studio.  Par exemple, vous pouvez ajouter un élément de menu contextuel à un élément de projet dans **Explorateur de solutions** et personnaliser l'élément de projet lorsqu'un développeur choisit l'élément de menu.  Pour plus d’informations, consultez [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Étendez les projets SharePoint  Pourquoi pas prévoir, par exemple, des gestionnaires d'événements pour effectuer des tâches spécifiques en cas d'ajout ou de suppression d'éléments dans les projets SharePoint ?  Pour plus d’informations, consultez [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md).  
  
-   Étendez le comportement d'empaquetage et de déploiement des éléments de projet et projets SharePoint.  Rien ne vous empêche, par exemple, de définir vos propres étapes de déploiement à exécuter lors du déploiement ou du retrait d'un projet, ou de réaliser des tâches personnalisées supplémentaires lorsque Visual Studio exécute certaines étapes de déploiement.  Pour plus d’informations, consultez [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## Tâches de développement courantes  
 Vous pouvez effectuer les tâches courantes suivantes dans les extensions du système de projet SharePoint :  
  
-   Enregistrez les données e type chaîne personnalisées avec des éléments de projet et dans plusieurs types de fichiers projet.  Pour plus d’informations, consultez [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertir un objet du système de projet SharePoint en un objet correspondant dans le modèle d'objet Automation Visual Studio ou dans le modèle d'objet Intégration, et vice versa.  Pour plus d’informations, consultez [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## Voir aussi  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  