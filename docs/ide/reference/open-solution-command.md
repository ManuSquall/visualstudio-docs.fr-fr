---
title: "Ouvrir une solution, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.opensolution"
helpviewer_keywords: 
  - "File.OpenSolution (commande)"
  - "Ouvrir une solution (commande)"
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Ouvrir une solution, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre une solution existante, après avoir fermé toute autre solution ouverte.  
  
## Syntaxe  
  
```  
File.OpenSolution filename  
```  
  
## Arguments  
 `Filename`  
 Obligatoire.  Chemin d'accès complet et nom de fichier de la solution à ouvrir.  
  
 La syntaxe de l'argument `filename` nécessite que les chemins d'accès comportant des espaces soient entourés de guillemets doubles.  
  
## Notes  
 La fonctionnalité de saisie semi\-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.  
  
## Exemple  
 Cet exemple ouvre la solution Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)