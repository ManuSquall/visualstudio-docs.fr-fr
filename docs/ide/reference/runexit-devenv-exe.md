---
title: "/Runexit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/runexit (commutateur de Devenv)"
  - "Devenv, /runexit (commutateur)"
  - "runexit (commutateur de Devenv)"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compile et exécute le projet ou la solution spécifiée, puis ferme l'environnement de développement intégré \(IDE\).  
  
## Syntaxe  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## Arguments  
 `SolutionName`  
 Obligatoire.  Chemin d'accès complet et nom d'un fichier solution.  
  
 `ProjectName`  
 Obligatoire.  Chemin d'accès complet et nom d'un fichier projet.  
  
## Notes  
 Compile et exécute la solution ou le projet spécifié en fonction des paramètres spécifiés pour la configuration de la solution active.  Ce commutateur réduit la fenêtre de l'IDE pendant l'exécution de la solution ou du projet et ferme cette fenêtre à la fin de leur exécution.  
  
-   Mettez les chaînes qui comprennent des espaces entre des guillemets doubles.  
  
-   Les informations résumées, y compris les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## Exemple  
 Cet exemple exécute la solution `MySolution` dans une fenêtre réduite de l'IDE en utilisant la configuration de déploiement active, puis ferme l'IDE.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)