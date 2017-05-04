---
title: "toLowerCase, m&#233;thode (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase (méthode)"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLowerCase, m&#233;thode (JavaScript)
Convertit tous les caractères alphabétiques d'une chaîne en minuscules.  
  
## Syntaxe  
  
```  
  
        strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## Notes  
 La méthode `toLowerCase` n'a aucun effet sur les caractères non alphabétiques.  
  
 L'exemple suivant illustre les effets de la méthode `toLowerCase` :  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [toLocaleLowerCase, méthode \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase, méthode \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)