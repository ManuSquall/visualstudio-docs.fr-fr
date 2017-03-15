---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/upgrade (commutateur de Devenv)"
  - "Devenv, /upgrade (commutateur)"
  - "upgrade (commutateur de Devenv)"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Met à jour le fichier solution et tous ses fichiers projet, ou le fichier projet spécifié, aux formats [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] actuels pour ces fichiers.  
  
## Syntaxe  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## Arguments  
 `SolutionFile`  
 Requis si vous mettez à niveau une solution entière avec ses projets.  Chemin d'accès et nom d'un fichier solution.  Vous pouvez entrer uniquement le nom du fichier solution, ou un chemin d'accès complet et le nom du fichier solution.  Si le dossier ou le fichier nommé n'existe pas encore, il sera créé.  
  
 `ProjectFile`  
 Requis si vous mettez à niveau un projet seul.  Chemin d'accès et nom d'un fichier projet dans la solution.  Vous pouvez entrer uniquement le nom du fichier projet, ou un chemin d'accès complet et le nom du fichier projet.  Si le dossier ou le fichier nommé n'existe pas encore, il sera créé.  
  
## Notes  
 Les sauvegardes sont créées et copiées automatiquement vers un répertoire nommé Backup, créé dans le répertoire actif.  
  
 Les solutions ou projets sous contrôle de code source doivent être extraits avant de pouvoir être mis à niveau.  
  
 L'utilisation du commutateur `/upgrade` ne démarre pas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Les résultats de la mise à niveau peuvent être vus dans le Rapport de mise à niveau pour le langage de développement de la solution ou du projet.  Aucune information d'erreur ou d'utilisation n'est retournée.  Pour plus d'informations sur la mise à niveau de projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], consultez [Comment : dépanner les échecs de mise à niveau de projets Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## Exemple  
 Cet exemple met à niveau un fichier solution nommé « MyProject.sln » dans votre dossier par défaut des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## Voir aussi  
 [Comment : dépanner les échecs de mise à niveau de projets Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)