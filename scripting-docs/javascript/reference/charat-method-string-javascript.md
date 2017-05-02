---
title: "charAt, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String (objet), retour de caractères"
  - "charAt (méthode)"
  - "caractères, retour d’une partie"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# charAt, m&#233;thode (String) (JavaScript)
Retourne le caractère situé à l'index spécifié.  
  
## Syntaxe  
  
```  
  
strObj. charAt(index)  
```  
  
## Paramètres  
 `strObj`  
 Obligatoire.  Tout objet `String` ou littéral de chaîne.  
  
 `index`  
 Obligatoire.  L'index de base zéro du caractère souhaité.  
  
## Notes  
 La méthode `charAt` retourne une valeur de caractère égale au caractère situé à l'`index` spécifié.  Le premier caractère d'une chaîne se trouve à l'index 0, le deuxième à l'index 1, et ainsi de suite.  Les valeurs d'`index` hors de la plage valide retournent une chaîne vide.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `charAt` :  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [String, objet](../../javascript/reference/string-object-javascript.md)