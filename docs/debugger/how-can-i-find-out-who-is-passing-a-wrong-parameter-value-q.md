---
title: "Comment puis-je savoir d&#39;o&#249; provient une valeur de param&#232;tre incorrecte&#160;? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "déboguer (C++), paramètres"
  - "fonctions (débogueur), détecter les valeurs de paramètre incorrectes"
  - "valeurs de paramètre, dépanner"
  - "paramètres (débogueur)"
  - "passer des paramètres, dépanner les valeurs erronées"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment puis-je savoir d&#39;o&#249; provient une valeur de param&#232;tre incorrecte&#160;?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Description du problème  
 Une valeur de paramètre incorrecte est passée à l'une de mes fonctions.  Cette fonction est appelée à partir de différents endroits.  Comment puis\-je savoir d'où provient la valeur incorrecte ?  
  
## Solution  
  
#### Pour résoudre ce problème  
  
1.  Définissez un point d'arrêt d'emplacement au début de la fonction.  
  
2.  Cliquez avec le bouton droit sur le point d'arrêt et sélectionnez **Condition**.  
  
3.  Dans la boîte de dialogue **Condition de point d'arrêt**, activez la case à cocher **Condition**.  Voir la rubrique sur la [Points d’arrêt avancés](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Entrez une expression, telle que `Var==3`, dans la zone de texte, où `Var` est le nom du paramètre qui contient la valeur incorrecte et où `3` correspond à la valeur incorrecte passée.  
  
5.  Activez la case d'option **est true**, puis cliquez sur le bouton **OK**.  
  
6.  Réexécutez le programme.  Le point d'arrêt provoque l'arrêt du programme au début de la fonction lorsque la valeur du paramètre `Var` est `3`.  
  
7.  Utilisez la fenêtre Pile des appels pour rechercher la fonction d'appel et naviguer jusqu'à son code source.  Pour plus d'informations, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).  
  
## Voir aussi  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/fr-fr/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Débogage du code natif](../debugger/debugging-native-code.md)