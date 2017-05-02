---
title: "slice, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice (méthode)"
  - "chaînes (Visual Studio), retourner des caractères"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# slice, m&#233;thode (String) (JavaScript)
Retourne une section de chaîne.  
  
## Syntaxe  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## Paramètres  
 `stringObj`  
 Requis.  Objet `String` ou littéral de chaîne.  
  
 `start`  
 Requis.  Index au début de la partie spécifiée de `stringObj`.  
  
 `end`  
 Optionnel.  Index à la fin de la partie spécifiée de `stringObj`.  La sous\-chaîne inclut tous les caractères jusqu'à celui indiqué par `end` \(non compris\).  Si cette valeur n'est pas spécifiée, la sous\-chaîne continue à la fin de `stringObj`.  
  
## Notes  
 La méthode `slice` retourne un objet `String` contenant la partie spécifiée de `stringObj`.  
  
 La méthode `slice` copie tous les caractères jusqu'au caractère \(non compris\) indiqué par `end`.  
  
 Si la valeur `start` est négative, la valeur utilisée est *length* \+ `start` où *length* représente la longueur de la chaîne.  Si la valeur `end` est négative, la valeur utilisée est *longueur* \+ `end`.  Si la valeur `end` est omise, la copie se poursuit jusqu'à la fin de `stringObj`.  Si `end` se produit avant `start`, aucun caractère n'est copié dans la nouvelle chaîne.  
  
## Exemple  
 Dans le premier exemple, la méthode `slice` retourne la chaîne entière.  Dans le second exemple, la méthode `slice` retourne la chaîne entière, à l'exception du dernier caractère.  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [Méthode slice \(tableau\)](../../javascript/reference/slice-method-array-javascript.md)