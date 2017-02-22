---
title: "/DebugExe (devenv.exe) | Microsoft Docs"
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
  - "/DebugExe (devenv.exe)"
  - "DebugExe (commutateur)"
  - "Devenv, /DebugExe (commutateur)"
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre le fichier exécutable spécifié à déboguer.  
  
## Syntaxe  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## Arguments  
 `ExecutableFile`  
 Obligatoire.  Chemin d'accès et nom de fichier d'un fichier .exe.  
  
 Si le fichier .exe est introuvable ou n'existe pas, aucun avertissement ou erreur n'est affiché et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] démarre normalement.  
  
## Notes  
 Tout chaîne qui suit le paramètre `ExecutableFile` est passée à ce fichier comme argument.  
  
## Exemple  
 L'exemple suivant ouvre le fichier en mode `MyApplication.exe` pour débogage  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)