---
title: "Array.from, fonction (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.from, fonction (Array) (JavaScript)
Retourne un tableau à partir d'un objet de type tableau ou pouvant être itéré.  
  
## Syntaxe  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### Paramètres  
 `arrayLike`  
 Obligatoire.  Objet de type tableau ou pouvant être itéré.  
  
 `mapfn`  
 Facultatif.  Fonction de mappage à appeler sur chaque élément dans `arrayLike`.  
  
 `thisArg`  
 Facultatif.  Spécifie l'objet `this` dans la fonction de mappage.  
  
## Notes  
 Le paramètre `arrayLike` doit être un objet avec des éléments indexés et une propriété `length` ou un objet pouvant être itéré, comme un objet `Set`.  
  
 La fonction de mappage facultative est appelée sur chaque élément du tableau.  
  
## Exemple  
 L'exemple suivant retourne un tableau à partir d'une collection de nœuds d'éléments DOM.  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## Exemple  
 L'exemple suivant retourne un tableau de caractères.  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## Exemple  
 L'exemple suivant retourne un tableau d'objets contenus dans la collection.  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la syntaxe de fonction Arrow et d'une fonction de mappage pour modifier la valeur des éléments.  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]