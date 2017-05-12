---
title: "D&#233;ploiement d&#39;une solution Office"
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
  - "déploiement ClickOnce (développement Office dans Visual Studio), à propos des déploiements de solutions ClickOnce"
  - "déploiement ClickOnce (développement Office dans Visual Studio), observateur d'événements"
  - "déploiement ClickOnce (développement Office dans Visual Studio), dépanner"
  - "déployer des applications (développement Office dans Visual Studio), observateur d'événements"
  - "déployer des applications (développement Office dans Visual Studio), solutions Office (Office System 2007)"
  - "déployer des applications (développement Office dans Visual Studio), dépanner"
  - "applications Office (développement Office dans Visual Studio), déployer des solutions Office"
  - "développement Office dans Visual Studio, déployer des solutions Office"
  - "développement Office dans Visual Studio, observateur d'événements"
  - "développement Office dans Visual Studio, dépanner"
  - "solutions Office (développement Office dans Visual Studio), déployer"
  - "solutions (développement Office dans Visual Studio), déployer des solutions Office (Office System 2007)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# D&#233;ploiement d&#39;une solution Office
  Vous pouvez déployer des solutions Office à l'aide des technologies de déploiement ClickOnce ou Windows Installer.  En utilisant ClickOnce, vous réduisez le nombre d'étapes que nécessitent le déploiement et la mise à jour de votre solution.  Si vous utilisez Windows Installer, vous pouvez contrôler la manière dont une solution est installée et les pages du programme d'installation qui s'affichent lorsque les utilisateurs installent votre solution.  
  
## Déploiement d'une solution en utilisant ClickOnce  
 Lorsque vous déployez une solution en utilisant ClickOnce, vous la publiez dans un emplacement central où les utilisateurs peuvent l'installer et l'exécuter.  Vous pouvez mettre à jour la solution sans avoir à distribuer un nouveau programme d'installation aux utilisateurs.  Cette option de déploiement est plus simple, mais vous ne pouvez pas afficher de pages d'installation personnalisées pour les utilisateurs.  En outre, les solutions doivent être installées plusieurs fois sur un ordinateur ayant plusieurs utilisateurs.  Consultez [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Déploiement d'une solution à l'aide de Windows Installer  
 Lorsque vous déployez une solution à l'aide de Windows Installer, vous devez distribuer un programme d'installation aux utilisateurs afin qu'ils installent la solution.  Le programme d'installation peut installer une solution pour tous les utilisateurs d'un ordinateur en même temps, plutôt que l'utilisateur actuel uniquement.  Vous avez également un peu plus de contrôle sur les options proposées aux utilisateurs lors de l'installation de votre solution.  Par exemple, vous pouvez afficher un contrat de licence ou permettre aux utilisateurs d'installer les composants spécifiques d'une solution.  Toutefois, si vous mettez à jour la solution, vous devez distribuer le programme d'installation.  Consultez [Déploiement d'une solution Office à l'aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## Voir aussi  
 [Sécurisation des solutions Office](../vsto/securing-office-solutions.md)   
 [Déploiement d'une solution Office à l'aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Déploiement d'une solution Office à l'aide de Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Dépannage du déploiement de solutions Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  