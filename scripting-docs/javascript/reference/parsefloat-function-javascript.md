---
title: "parseFloat, fonction (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat (méthode)"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# parseFloat, fonction (JavaScript)
Convertit une chaîne en un nombre à virgule flottante.  
  
## Syntaxe  
  
```  
parseFloat(numString)   
```  
  
## Notes  
 L'argument `numString` requis est une chaîne qui contient un nombre à virgule flottante.  
  
 La fonction `parseFloat` retourne une valeur numérique égale au nombre contenu dans `numString`.  Si aucun préfixe de l'argument `numString` ne peut être interprété comme un nombre à virgule flottante, la valeur `NaN` \(Not a Number, pas un nombre\) est retournée.  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Effectuez un test avec `NaN` au moyen de la fonction `isNaN`.  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Voir aussi  
 [Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Fonction parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [String, objet](../../javascript/reference/string-object-javascript.md)