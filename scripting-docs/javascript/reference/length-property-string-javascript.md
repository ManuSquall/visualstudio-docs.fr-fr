---
title: "length, propri&#233;t&#233; (String) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "chaînes (Visual Studio), longueur"
  - "Length (propriété)"
  - "length (propriété) (String)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# length, propri&#233;t&#233; (String) (JavaScript)
Retourne la longueur d'un objet `String`.  
  
> [!WARNING]
>  Les chaînes JavaScript étant immuables, la longueur d'une chaîne ne peut pas être modifiée.  
  
## Syntaxe  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## Notes  
 La propriété `length` contient un entier indiquant le nombre de caractères dans l'objet `String`.  Le dernier caractère de l'objet `String` a un index égal à `length` \- 1.  
  
## Exemple  
 Le code suivant montre comment utiliser `length`.  Les chaînes JavaScript sont immuables et ne peuvent donc pas être modifiés sur place.  Vous pouvez toutefois écrire la chaîne inversée dans un tableau et appeler `join` avec le caractère vide, ce qui produit une chaîne sans caractère de séparation.  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]