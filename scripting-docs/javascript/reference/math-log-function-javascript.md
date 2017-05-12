---
title: "Math.log, fonction (JavaScript) | Microsoft Docs"
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
  - "log"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "log (méthode)"
  - "Math (objet)"
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Math.log, fonction (JavaScript)
Retourne le logarithme naturel \(base `e`\) d'un nombre.  
  
## Syntaxe  
  
```  
Math.log(number)   
```  
  
#### Paramètres  
 nombre  
 Nombre.  
  
## Valeur de retour  
 Si `number` est positif, cette fonction retourne le logarithme népérien du nombre.  Si `number` est négatif, cette fonction retourne `NaN`.  Si `number` est 0, cette fonction retourne `-Infinity`.  
  
## Exemple  
 Le code suivant montre comment utiliser cette fonction.  
  
```javascript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)  
  
## Voir aussi  
 [Math.sqrt, fonction](../../javascript/reference/math-sqrt-function-javascript.md)