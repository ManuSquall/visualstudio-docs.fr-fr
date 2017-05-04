---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Les outils sharepoint dans Visual Studio répondent aux besoins de nombreux scénarios de développement d'applications.  Il est possible, cependant, qu'elles n'offrent pas toutes les fonctionnalités dont vous ou d'autres développeurs avez besoin.  Dans ce cas, il suffit d'étendre les outils SharePoint de manière à bénéficier des fonctionnalités voulues.  
  
## Extension des outils SharePoint  
 Vous pouvez étendre le système de projet SharePoint et le nœud **Connexions SharePoint** dans la fenêtre l'**Explorateur de serveurs**.  
  
### Extension du système de projet SharePoint  
 Visual Studio inclut un jeu de modèles de projet et de modèles d'élément que vous pouvez utiliser pour créer des solutions SharePoint.  Il existe, par exemple, des modèles pour les récepteurs d'événements, les définitions de listes, les flux de travail et les composants WebPart.  Toutefois, vous pouvez également définir vos propres types d'éléments de projet SharePoint pour la création de composants SharePoint tels que des champs ou des actions personnalisées.  Vous avez également la possibilité de créer des extensions pour les types d'éléments de projet SharePoint qui sont déjà installés dans Visual Studio et de créer des extensions pour les projets SharePoint.  
  
 Pour plus d'informations, consultez [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Extension du nœud Connexions SharePoint dans l'Explorateur de serveurs  
 Dans Visual Studio, vous pouvez utiliser le nœud de**Connexions SharePoint** dans la fenêtre d'**Explorateur de serveurs** pour afficher plusieurs des composants d'un ou plusieurs sites sharepoint locaux dans une arborescence hiérarchique. Vous pouvez étendre le nœud de **Connexions SharePoint** des façons suivantes :  
  
-   En ajoutant vos propres nœuds.  Cela peut être utile si vous comptez afficher des composants de sites SharePoint non visibles par défaut.  
  
-   En étendant des nœuds existants.  Par exemple, vous pouvez ajouter un nouveau nœud enfant à un nœud existant ou vous pouvez ajouter un élément de menu contextuel à un nœud et effectuer des tâches lorsqu'un développeur clique sur l'élément de menu.  
  
 Pour plus d'informations, consultez [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Configuration requise pour l'ordinateur de développement  
 Pour créer des extensions pour les outils sharepoint, votre ordinateur de développement présente les mêmes spécifications pour créer des solutions SharePoint dans Visual Studio.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Nous vous recommandons également d'installer le [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Le Kit de développement logiciel \(SDK\) contient des modèles de projet et des outils permettant l'extension de Visual Studio.  Il offre, en particulier, un modèle de projet qui simplifie la création d'un package VSIX \(Visual Studio Extension\).  Les packages VSIX constituent la meilleure façon de déployer des extensions Visual Studio dans Visual Studio.  Toutes les extensions d'outils SharePoint doivent être déployées à l'aide des packages VSIX.  L'ensemble des procédures pas à pas décrites dans cette documentation supposent que vous avez installé le [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  
  
 Pour télécharger le Kit de développement logiciel \(SDK\), consultez la page Web suivante \(éventuellement en anglais\) : [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562).  Pour plus d'informations au sujet des extensions Visual Studio, consultez [Développement d’extensions Visual Studio](../Topic/Developing%20Visual%20Studio%20Extensions.md).  
  
## Voir aussi  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  