---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project (commutateur de Devenv)"
  - "projets de déploiement, spécifier"
  - "Devenv, /project (commutateur)"
  - "commutateur de Devenv (/project)"
  - "projets (Visual Studio), générer"
  - "projets (Visual Studio), nettoyer"
  - "projets (Visual Studio), régénérer"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Identifie un projet à générer, nettoyer, régénérer ou déployer dans la configuration de solution spécifiée.  
  
## Syntaxe  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## Arguments  
 \/build  
 Génère le projet spécifié par `/project` `ProjName`.  
  
 \/clean  
 Nettoie tous les fichiers et répertoires de sortie intermédiaires qui ont été créés au cours d'une génération.  
  
 \/rebuild  
 Nettoie puis génère le projet spécifié par `/project` `ProjName`.  
  
 \/deploy  
 Spécifie que le projet doit être déployé après une génération ou une régénération.  
  
 `SolnConfigName`  
 Obligatoire.  Le nom de la configuration de solution qui sera appliquée à la solution nommée dans `SolutionName`.  
  
 `SolutionName`  
 Obligatoire.  Chemin d'accès complet et nom du fichier solution.  
  
 \/project`ProjName`  
 Facultatif.  Chemin d'accès et nom d'un fichier projet dans la solution.  Vous pouvez entrer un chemin d'accès relatif du dossier `SolutionName` au fichier projet, le nom complet du projet ou le chemin d'accès complet et le nom du fichier projet.  
  
 \/projectconfig `ProjConfigName`  
 Facultatif.  Le nom d'une configuration de build de projet à appliquer au `/project` nommé.  
  
## Notes  
  
-   Doit être utilisé dans le cadre d'une commande `devenv /build`, \/`clean`, `/rebuild` ou `/deploy`.  
  
-   Mettez les chaînes qui comprennent des espaces entre des guillemets doubles.  
  
-   Les informations résumées pour les générations, y compris les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## Exemple  
 Cet exemple génère le projet `CSharpConsoleApp`, à l'aide de la configuration de build de projet `Debug` dans la configuration de solution `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)