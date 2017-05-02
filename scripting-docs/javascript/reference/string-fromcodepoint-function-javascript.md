---
title: "String.fromCodePoint, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.fromCodePoint, fonction (JavaScript)
Retourne la chaîne associée avec un point de code Unicode UTF\-16.  
  
## Syntaxe  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### Paramètres  
 `…codePoints`  
 Obligatoire.  Paramètre rest qui spécifie une ou plusieurs valeurs de point de code UTF\-16.  
  
## Notes  
 Cette fonction génère une exception `RangeError` si `...codePoints` n'est pas un point de code UTF\-16 valide.  
  
## Exemple  
 L'exemple suivant montre comment utiliser la fonction `fromCodePoint`.  
  
```javascript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]