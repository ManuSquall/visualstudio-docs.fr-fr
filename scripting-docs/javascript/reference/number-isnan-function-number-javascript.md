---
title: "Number.isNaN, fonction (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Number.isNaN, fonction (Number) (JavaScript)
Retourne une valeur booléenne qui indique si une valeur est la valeur réservée `NaN` \(pas un nombre\).  
  
## Syntaxe  
  
```  
Number.isNaN(numValue)   
```  
  
#### Paramètres  
 `numValue`  
 Obligatoire.  Valeur à tester par rapport à `NaN`.  
  
## Valeur de retour  
 `true` si la valeur convertie en type `Number` est la valeur `NaN`, sinon `false`.  
  
## Notes  
 Vous utilisez généralement cette méthode pour tester les valeurs de retour des méthodes `parseInt` et `parseFloat`.  
  
 `Number.isNaN` corrige les problèmes avec la fonction `isNaN` globale.  `Number.isNaN` convertit uniquement son argument en type Number après l'avoir comparé à `NaN`.  Par conséquent, elle retourne `true` si et seulement si l'argument passé a exactement la même valeur que `NaN`.  La fonction `isNaN` globale convertit son argument en type Number avant la comparaison, ce qui peut aboutir à des valeurs autres que des nombres qui retournent `true`, alors qu'elles peuvent ne pas retourner `true` pour `Number.isNaN`.  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)  
  
## Exemple  
  
```javascript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```