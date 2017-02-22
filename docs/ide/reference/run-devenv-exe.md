---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r (commutateur de Devenv)"
  - "/run (Devenv)"
  - "applications (Visual Studio), exécuter"
  - "Devenv, /run (commutateur)"
  - "/r (commutateur de Devenv)"
  - "run (commutateur de Devenv)"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compile et exécute la solution ou le projet spécifié.  
  
## Syntaxe  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## Arguments  
 `SolutionName`  
 Obligatoire.  Chemin d'accès complet et nom d'un fichier solution.  
  
 `ProjectName`  
 Obligatoire.  Chemin d'accès complet et nom d'un fichier projet.  
  
## Notes  
 Compile et exécute la solution ou le projet spécifié en fonction des paramètres spécifiés pour la configuration de la solution active.  Ce commutateur lance l'environnement de développement intégré \(IDE\) et le maintient actif à la fin de l'exécution du projet ou de la solution.  
  
-   Mettez les chaînes qui comprennent des espaces entre des guillemets doubles.  
  
-   Les informations résumées, y compris les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## Exemple  
 Cet exemple exécute la solution `MySolution` en utilisant la configuration de déploiement active.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)