---
title: "toUpperCase, m&#233;thode (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "toUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUpperCase (méthode)"
ms.assetid: 4fd4ccc3-e794-498a-9db1-baf48fc1dda1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# toUpperCase, m&#233;thode (String) (JavaScript)
Convertit tous les caractères alphabétiques d'une chaîne en majuscules.  
  
## Syntaxe  
  
```  
  
        strVariable.toUpperCase()  
"String Literal".toUpperCase()   
```  
  
## Notes  
 La méthode `toUpperCase` n'a aucun effet sur les caractères non alphabétiques.  
  
## Exemple  
 L'exemple suivant illustre les effets de la méthode `toUpperCase` :  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1.toUpperCase();  
document.write(str2);  
  
// Output: THIS IS A STRING.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [toLocaleUpperCase, méthode \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [Méthode toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)