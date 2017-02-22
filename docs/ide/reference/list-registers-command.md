---
title: "Afficher les registres, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters (commande)"
  - "Afficher les registres (commande)"
  - "ListRegisters (commande)"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Afficher les registres, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Affiche la valeur des registres sélectionnés et vous permet de modifier la liste de registres à afficher.  
  
## Syntaxe  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## Commutateurs  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 Affiche les valeurs du `register` ou `registerGroup` spécifié.  Si aucun `register` ou `registerGroup` n'est spécifié, la liste par défaut de registres est affichée.  Si aucun commutateur n'est spécifié, le comportement est le même.  Par exemple :  
  
 `Debug.ListRegisters /Display eax`  
  
 est équivalent à  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 Affiche tous les groupes de registres dans la liste.  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 Ajoute une ou plusieurs valeurs de `register` ou `registerGroup` dans la liste.  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 Supprime une ou plusieurs valeurs de `register` ou `registerGroup` de la liste.  
  
## Notes  
 L'alias `r` peut être utilisé à la place de `Debug.ListRegisters`.  
  
## Exemple  
 Cet exemple utilise l'alias `Debug.ListRegisters` `r` pour afficher les valeurs du groupe de registres `Flags`.  
  
```  
r /Display Flags  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Concepts de base du débogage : fenêtre Registres](../../debugger/debugging-basics-registers-window.md)   
 [Comment : utiliser la fenêtre Registres](../../debugger/how-to-use-the-registers-window.md)