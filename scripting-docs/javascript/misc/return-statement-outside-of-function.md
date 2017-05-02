---
title: "Instruction &#39;return&#39; en dehors de la fonction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Instruction &#39;return&#39; en dehors de la fonction
Vous avez utilisé une instruction `return` dans la portée globale de votre code.  L'instruction `return` ne doit apparaître que dans le corps d'une fonction.  
  
 Appeler une fonction à l'aide de l'opérateur `()` est une expression.  Toutes les expressions ont des valeurs ; l'instruction `return` est utilisée pour spécifier la valeur retournée par une fonction.  Sa forme générale est la suivante :  
  
```  
  
return [ expression ];  
```  
  
 Lorsque l'instruction `return` est exécutée, *expression* est évalué et retourné comme valeur de la fonction.  S'il n'existe aucune expression, **undefined** est retourné.  
  
 L'exécution de la fonction s'arrête lorsque l'instruction `return` est exécutée, même s'il reste d'autres instructions dans le corps de la fonction.  Il existe une exception à cette règle : si l'instruction **return** apparaît au sein d'un bloc **try** et s'il existe un bloc **finally** correspondant, le code figurant dans le bloc **finally** sera exécuté avant que la fonction retourne une valeur.  
  
 Si une fonction retourne une valeur car elle atteint la fin du corps de la fonction sans exécuter une instruction `return`, la valeur retournée est la valeur **undefined** \(cela signifie que le résultat de la fonction ne peut pas être utilisé dans le cadre d'une longue expression\).  
  
### Pour corriger cette erreur  
  
-   Supprimez l'instruction `return` du corps principal de votre code \(la portée globale\).  
  
## Voir aussi  
 [return, instruction](../../javascript/reference/return-statement-javascript.md)   
 [Objet de function](../../javascript/reference/function-object-javascript.md)   
 [caller, propriété \(Function\)](../../javascript/reference/caller-property-function-javascript.md)