---
title: "Impossible d&#39;assigner &#224; un r&#233;sultat de fonction | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5003"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Impossible d&#39;assigner &#224; un r&#233;sultat de fonction
Vous avez tenté d'assigner une valeur au résultat d'une fonction.  Le résultat d'une fonction peut être assigné à une variable, mais il ne peut pas être utilisé en tant que variable.  Si vous voulez assigner une nouvelle valeur à la fonction elle\-même, ne mettez pas de parenthèses \(l'opérateur d'appel de fonction\).  L'exemple suivant illustre une situation dans laquelle cette erreur est générée.  
  
```  
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### Pour corriger cette erreur  
  
-   *N'assignez pas* la valeur du résultat d'un appel de fonction.  Toutefois, vous pouvez assigner le résultat de l'appel de fonction à une *variable*.  
  
    ```javascript  
    myVar = myFunction(42);  
    ```  
  
-   Il est également possible d'assigner la fonction elle\-même \(et non sa valeur de retour\) à une variable.  
  
    ```javascript  
    myFunction = new Function("return 42;");  
    ```  
  
## Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)   
 [Écriture de code JavaScript](../../javascript/writing-javascript-code.md)   
 [Fonctions](../../javascript/functions-javascript.md)