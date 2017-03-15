---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild (commutateur de Devenv)"
  - "applications (Visual Studio), régénérer"
  - "Devenv, /rebuild (commutateur)"
  - "projets (Visual Studio), régénérer"
  - "/rebuild (commutateur de Devenv)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nettoie puis génère la configuration de solution spécifiée.  
  
## Syntaxe  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## Arguments  
 `SolnConfigName`  
 Requis.  Nom de la configuration de solution qui sera utilisée pour régénérer la solution nommée dans `SolutionName`.  
  
 `SolutionName`  
 Requis.  Chemin d'accès complet et nom du fichier solution.  
  
 \/project `ProjName`  
 Optionnel.  Chemin d'accès et nom d'un fichier projet dans la solution.  Vous pouvez entrer un chemin d'accès relatif du dossier `SolutionName` au fichier projet, le nom complet du projet ou le chemin d'accès complet et le nom du fichier projet.  
  
 \/projectconfig `ProjConfigName`  
 Optionnel.  Le nom d'une configuration de build de projet à utiliser lors de la régénération du `/project` nommé.  
  
## Notes  
  
-   Ce commutateur exécute la même fonction que la commande de menu **Régénérer la solution** dans l'environnement de développement intégré \(IDE\).  
  
-   Mettez les chaînes qui comprennent des espaces entre des guillemets doubles.  
  
-   Les informations résumées pour les nettoyages et les générations, y compris les erreurs, peuvent être affichées dans la fenêtre **Commande**, ou dans tout fichier journal spécifié avec le commutateur `/out`.  
  
## Exemple  
 Cet exemple nettoie et régénère le projet `CSharpWinApp`, à l'aide de la configuration de build de projet `Debug` dans la configuration de solution `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)