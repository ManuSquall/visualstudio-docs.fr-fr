---
title: "slice, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "index de base zéro"
  - "Array (objet)"
  - "slice (méthode)"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# slice, m&#233;thode (Array) (JavaScript)
Retourne une section d'un tableau.  
  
## Syntaxe  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## Paramètres  
 `arrayObj`  
 Obligatoire.  Objet `Array`.  
  
 `start`  
 Obligatoire.  Début de la partie spécifiée de `arrayObj`.  
  
 `end`  
 Facultatif.  Fin de la partie spécifiée de `arrayObj`.  
  
## Notes  
 La méthode `slice` retourne un objet `Array` contenant la partie spécifiée de `arrayObj`.  
  
 La méthode `slice` copie tous les éléments jusqu'à l'élément indiqué par `end`, à l'exclusion de ce dernier.  Si la valeur `start` est négative, la valeur utilisée est `length` \+ `start`, où `length` représente la longueur du tableau.  Si la valeur `end` est négative, la valeur utilisée est `length` \+ `end`, où `length` représente la longueur du tableau.  Si la valeur `end` est omise, l'extraction se poursuit jusqu'à la fin d'`arrayObj`.  Si `end` se produit avant `start`, aucun élément n'est copié dans le nouveau tableau.  
  
## Exemple  
 Les exemples suivants illustrent l'utilisation de la méthode `slice`.  Dans le premier exemple, tous les éléments de `myArray`, à l'exclusion du dernier, sont copiés dans `newArray`.  Dans le deuxième exemple, seuls les deux derniers éléments de `myArray` sont copiés dans `newArray`.  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [slice, méthode \(String\)](../../javascript/reference/slice-method-string-javascript.md)   
 [String, objet](../../javascript/reference/string-object-javascript.md)