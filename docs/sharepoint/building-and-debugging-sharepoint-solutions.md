---
title: "G&#233;n&#233;ration et d&#233;bogage de solutions SharePoint"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement SharePoint dans Visual Studio, générer et déboguer"
  - "développement SharePoint dans Visual Studio, débogage"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# G&#233;n&#233;ration et d&#233;bogage de solutions SharePoint
  En général, les processus de génération et de débogage de solutions SharePoint sont les mêmes que pour les autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Les rubriques de cette section expliquent les différences qui persistent.  
  
## Sortie de projet pour les solutions SharePoint  
 La génération de solutions SharePoint crée des assemblys et un fichier de package de solution \(.wsp\).  Le tableau suivant reprend les emplacements de ces fichiers au cours d'une génération.  
  
|Élément de génération|Dossier de sortie|  
|---------------------------|-----------------------|  
|Assembly, base de données de programme \(PDB\) et fichiers .wsp.|*ProjectName*\\ bin\\debug ou *ProjectName*\\ bin\\release|  
|Fichiers d'éléments de projet SharePoint.|*ProjectName*\\ package\\debug ou *ProjectName*\\ package\\release|  
|Générer des fichiers intermédiaires.|*ProjectName*\\ obj\\debug ou *ProjectName*\\ obj\\release|  
|Empaqueter des fichiers intermédiaires.|*ProjectName*\\ pkgobj\\debug ou *ProjectName*\\ pkgobj\\release|  
  
## Génération de solutions SharePoint  
 Pour générer des solutions SharePoint, la version correcte du serveur SharePoint doit être installée sur l'ordinateur de développement.  Sinon, la génération de solutions SharePoint est identique à la génération d'autres types de projets dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Pour plus d'informations, consultez [Comment : générer des solutions SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## Débogage et test de solutions SharePoint  
 Avant le débogage, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copie le package .wsp vers le serveur SharePoint, active les fonctionnalités relatives aux applications Web et au site, puis dans certains cas, démarre le projet.  Dans d'autres cas, vous devrez peut\-être ouvrir le projet manuellement.  Pour plus d’informations, consultez [Dépannage des solutions SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) et [Débogage de solutions SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Vérification et débogage des solutions SharePoint à l'aide des fonctions ALM  
 Les fonctionnalités de Visual Studio ALM telles que le test unitaire et l'IntelliTrace permettent de définir plus précisément des problèmes dans vos solutions de SharePoint.  Le profilage vous permet de rechercher et identifier les domaines problématiques en termes de performance dans vos solutions SharePoint.  Pour plus d’informations, consultez [Vérification et débogage du code SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) et [Profilage des performances des applications SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## Sécurité pendant le processus de génération  
 Pour empaqueter ou déployer des solutions SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] doit être autorisé à copier des fichiers vers le serveur SharePoint.  Vous devez exécuter [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en tant que processus élevé et votre compte d'utilisateur doit être un Administrateur de collections de sites sur le serveur SharePoint.  De plus, vous devez spécifier si votre projet est une solution bac à sable \(sandbox\) ou une solution de batterie.  Pour plus d'informations, consultez [Différences entre les solutions bac à sable &#40;sandbox&#41; et les solutions de batterie](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Utilisation de la commande Nettoyer  
 Lorsqu'une solution SharePoint est installée sur un serveur SharePoint pour le débogage, la commande **Nettoyer** ne désinstalle pas la solution.  À la place, vous devez désactiver les fonctionnalités via la configuration SharePoint.  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Parcours des connexions SharePoint à l'aide de l'Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  