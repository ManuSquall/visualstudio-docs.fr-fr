---
title: "Imprimer, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print (commande)"
  - "Imprimer (commande)"
  - "Print (méthode)"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Imprimer, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Évalue une expression ou affiche le texte spécifié.  
  
## Syntaxe  
  
```  
Debug.Print text  
```  
  
## Arguments  
 `text`  
 Obligatoire.  Expression à évaluer ou texte à afficher.  
  
## Notes  
 Vous pouvez utiliser le point d'interrogation \(?\) comme un alias pour cette commande.  Ainsi, la commande  
  
```  
>Debug.Print expA  
```  
  
 peut également être écrite  
  
```  
>? expA  
```  
  
 Les deux versions de cette commande retournent la valeur courante de l'expression `expA`.  
  
## Exemple  
  
```  
>Debug.Print varA  
```  
  
## Voir aussi  
 [Évaluer l'instruction, commande](../../ide/reference/evaluate-statement-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)