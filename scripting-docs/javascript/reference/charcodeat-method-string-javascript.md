---
title: "charCodeAt, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt (méthode)"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# charCodeAt, m&#233;thode (String) (JavaScript)
Retourne la valeur Unicode du caractère à l'emplacement spécifié.  
  
## Syntaxe  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## Paramètres  
 `strObj`  
 Obligatoire.  Tout objet `String` ou littéral de chaîne.  
  
 `index`  
 Obligatoire.  L'index de base zéro du caractère souhaité.  S'il n'existe aucun caractère à l'index spécifié, la valeur `NaN` est retournée.  
  
## Notes  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `charCodeAt`.  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [Fonction String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)