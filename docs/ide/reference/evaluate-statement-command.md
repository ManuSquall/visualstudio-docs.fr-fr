---
title: "&#201;valuer l&#39;instruction, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement (commande)"
  - "Évaluer l'instruction (commande)"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# &#201;valuer l&#39;instruction, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Évalue et affiche l'instruction donnée.  
  
## Syntaxe  
  
```  
Debug.EvaluateStatement text   
```  
  
## Arguments  
 `text`  
 Obligatoire.  Représente l'instruction à évaluer.  
  
## Notes  
 La fenêtre utilisée pour entrer la commande **EvaluateStatement** détermine si un signe égal \(\=\) est interprété comme un opérateur de comparaison ou comme un opérateur d'assignation.  
  
 Dans la fenêtre de **Commande**, un signe égal \(\=\) est interprété comme un opérateur de comparaison.  Ainsi par exemple, si les valeurs des variables `a` et `b` sont différentes, la commande  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 retournera la valeur `false`.  
  
 Dans la fenêtre **Exécution**, par contraste, un signe égal \(\=\) est interprété comme un opérateur d'assignation.  Ainsi, la commande  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 affectera à la variable `a` la valeur de la variable `b`.  
  
## Exemple  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## Voir aussi  
 [Imprimer, commande](../../ide/reference/print-command.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)