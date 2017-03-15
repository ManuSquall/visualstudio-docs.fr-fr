---
title: "Atteindre, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto (commande)"
  - "Atteindre (commande)"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Atteindre, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Déplace le curseur à la ligne spécifiée.  
  
## Syntaxe  
  
```  
Edit.GoTo [linenumber]  
```  
  
## Arguments  
 `linenumber`  
 Facultatif.  Nombre entier représentant le numéro de la ligne à atteindre.  
  
## Notes  
 La numérotation des lignes débute à 1.  Si la valeur de l'argument `linenumber` est inférieure à 1, la première ligne est affichée.  Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.  
  
 Si aucune valeur n'est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s'affiche.  
  
 L'alias de cette commande est GoToLn.  
  
## Exemple  
  
```  
>Edit.GoTo 125  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)