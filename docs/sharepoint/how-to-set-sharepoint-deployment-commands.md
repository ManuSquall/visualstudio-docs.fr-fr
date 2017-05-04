---
title: "Comment&#160;: d&#233;finir des commandes de d&#233;ploiement SharePoint | Microsoft Docs"
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
  - "développement SharePoint dans Visual Studio, déployer"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Comment&#160;: d&#233;finir des commandes de d&#233;ploiement SharePoint
  Vous pouvez personnaliser le processus de déploiement en définissant des commandes de prédéploiement et de post\-déploiement.  Ces commandes sont exécutées avant et après les autres actions de déploiement lorsque vous déboguez des solutions SharePoint depuis Visual Studio.  
  
### Pour ajouter une commande de prédéploiement  
  
1.  Dans la barre de menus, choisissez **Projet**, *ProjectName* **Propriétés**.  
  
2.  Choisissez l'onglet **SharePoint**.  
  
3.  Dans la zone de texte **Ligne de commande de pré\-déploiement**, entrez des commandes MS\-DOS ou MSBuild pour personnaliser cette étape.  
  
     Pour afficher, par exemple, le contenu du répertoire avant que le déploiement prenne effet, entrez **dir**.  
  
### Pour ajouter une commande de post\-déploiement  
  
1.  Dans la barre de menus, choisissez **Projet**, *ProjectName* **Propriétés**.  
  
2.  Choisissez l'onglet **SharePoint**.  
  
3.  Dans la zone de texte **Ligne de commande de post\-déploiement**, entrez des commandes MS\-DOS ou MSBuild pour personnaliser cette étape.  
  
     Pour afficher, par exemple, le contenu du répertoire une fois le déploiement réalisé, entrez **dir**.  Pour copier l'assembly à partir du répertoire de build à l'aide d'une variable MSBuild, entrez **copy $\(TargetPath\) c:\\DeploymentDirectory**.  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  