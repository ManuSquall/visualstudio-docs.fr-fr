---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean (commutateur de Devenv)"
  - "builds (Team System), nettoyer les fichiers"
  - "clean (commutateur de Devenv)"
  - "Devenv, /clean (commutateur)"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nettoie tous les fichiers et répertoires de sortie intermédiaires.  
  
## Syntaxe  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## Arguments  
 `FileName`  
 Obligatoire.  Chemin d'accès et nom complets du fichier solution ou fichier projet.  
  
 \/project `ProjName`  
 Facultatif.  Chemin d'accès et nom d'un fichier projet dans la solution.  Vous pouvez entrer un chemin d'accès relatif du dossier `SolutionName` au fichier projet, le nom complet du projet ou le chemin d'accès complet et le nom du fichier projet.  
  
 \/projectconfig `ProjConfigName`  
 Facultatif.  Le nom d'une configuration de build de projet à utiliser lors du nettoyage du `/project` nommé.  
  
## Notes  
 Ce commutateur exécute la même fonction que la commande de menu **Nettoyer la solution** dans l'environnement de développement intégré \(IDE\).  
  
 Mettez les chaînes qui comprennent des espaces entre des guillemets doubles.  
  
 Les informations résumées pour les nettoyages et les générations, y compris les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## Exemple  
 Le premier exemple nettoie la solution `MySolution`, à l'aide de la configuration par défaut spécifiée dans le fichier solution.  
  
 Ce deuxième exemple nettoie le projet `CSharpConsoleApp`, à l'aide de la configuration de build de projet `Debug` dans la configuration de solution `Debug` de `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)