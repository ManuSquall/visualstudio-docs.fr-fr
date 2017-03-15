---
title: "Ouvrir un projet, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openproject"
helpviewer_keywords: 
  - "File.OpenProject (commande)"
  - "op (commande)"
  - "Ouvrir un projet (commande)"
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Ouvrir un projet, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre un projet existant.  
  
## Syntaxe  
  
```  
File.OpenProject filename  
```  
  
## Arguments  
 `filename`  
 Obligatoire.  Chemin d'accès complet et nom du projet à ouvrir.  
  
 La syntaxe de l'argument `filename` nécessite que les chemins d'accès comportant des espaces soient entourés de guillemets doubles.  
  
## Notes  
 La fonctionnalité de saisie semi\-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.  
  
 Cette commande n'est pas disponible lors du débogage.  
  
## Exemple  
 Cet exemple ouvre le projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)