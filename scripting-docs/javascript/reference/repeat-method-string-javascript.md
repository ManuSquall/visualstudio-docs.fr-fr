---
title: "repeat, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# repeat, m&#233;thode (String) (JavaScript)
Retourne un nouvel objet String avec une valeur égale à la chaîne d'origine répétée le nombre de fois spécifié.  
  
## Syntaxe  
  
```  
stringObj.repeat(count);  
```  
  
#### Paramètres  
 `stringObj`  
 Obligatoire.  Objet String.  
  
 `count`  
 Obligatoire.  Nombre de répétitions de la chaîne d'origine dans la chaîne retournée.  
  
## Exceptions  
 Cette méthode génère une erreur RangeError si et seulement si l'argument est négatif ou \+Infini.  
  
## Notes  
 La méthode `repeat` concatène la chaîne d'origine dans la nouvelle chaîne le nombre de fois spécifié par `count`.  
  
 Cette méthode génère une erreur si `count` n'est pas un nombre positif inférieur à `Infinity`.  
  
## Exemple  
  
```javascript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]