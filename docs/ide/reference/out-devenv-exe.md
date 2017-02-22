---
title: "/Out (devenv.exe) | Microsoft Docs"
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
  - "/out (commutateur de Devenv)"
  - "générations (Visual Studio), erreurs"
  - "générations (Visual Studio), journaux"
  - "Devenv, /out (commutateur)"
  - "journaux d'erreur (Visual Studio)"
  - "journaux d'erreur (Visual Studio), erreurs de génération à partir de la ligne de commande"
  - "erreurs (Visual Studio), builds"
  - "out (commutateur de Devenv)"
  - "fichiers de sortie, erreurs de build"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie un fichier pour stocker et afficher les erreurs qui se produisent lorsque vous exécutez, générez, régénérez ou déployez une solution.  
  
## Syntaxe  
  
```  
devenv /out FileName  
```  
  
## Arguments  
 `FileName`  
 Obligatoire.  Chemin d'accès et nom du fichier où seront enregistrées les erreurs rencontrées au cours de la génération d'un exécutable.  
  
## Notes  
 Si un fichier spécifié n'existe pas, ce fichier est créé automatiquement.  Si le fichier existe déjà, les résultats sont ajoutés au contenu existant du fichier.  
  
 Les erreurs de build de ligne de commande sont affichées dans la fenêtre **Commande** et dans la vue Générateur de solutions de la fenêtre **Sortie**.  Cette option s'avère utile si vous exécutez des générations en mode autonome et que vous souhaitez vérifier le résultat.  
  
## Exemple  
 Cet exemple exécute `MySolution` et écrit les erreurs dans le fichier `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)