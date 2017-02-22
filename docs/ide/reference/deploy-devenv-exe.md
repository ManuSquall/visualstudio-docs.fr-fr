---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy (commutateur de Devenv)"
  - "deploy (commutateur de Devenv)"
  - "déployer des applications (Visual Studio), après la génération"
  - "Devenv, /deploy (commutateur)"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Déploie une solution après une génération ou une régénération.  S'applique aux projets de code managé uniquement.  
  
## Syntaxe  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## Arguments  
 `SolnConfigName`  
 Obligatoire.  Nom de la configuration de solution qui sera utilisée pour générer la solution nommée dans `SolutionName`.  
  
 `SolutionName`  
 Obligatoire.  Chemin d'accès complet et nom du fichier solution.  
  
 \/project `ProjName`  
 Facultatif.  Chemin d'accès et nom d'un fichier projet dans la solution.  Vous pouvez entrer un chemin d'accès relatif du dossier `SolutionName` au fichier projet, le nom complet du projet ou le chemin d'accès complet et le nom du fichier projet.  
  
 \/projectconfig `ProjConfigName`  
 Facultatif.  Le nom d'une configuration de build de projet à utiliser lors de la génération du `/project` nommé.  
  
## Notes  
 Le projet spécifié doit être un projet de déploiement.  Si ce n'est pas le cas, lorsque le projet généré est passé en vue de son déploiement, une erreur se produit et le déploiement échoue.  
  
 Mettez les chaînes qui comprennent des espaces entre des guillemets doubles.  
  
 Les informations résumées pour les générations, y compris les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## Exemple  
 Cet exemple déploie le projet `CSharpConsoleApp`, à l'aide de la configuration de build de projet `Release` dans la configuration de solution `Release` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)