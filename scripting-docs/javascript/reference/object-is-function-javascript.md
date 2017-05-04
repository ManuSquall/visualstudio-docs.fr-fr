---
title: "Object.is, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.is, fonction (JavaScript)
Retourne une valeur qui indique si deux valeurs sont identiques.  
  
## Syntaxe  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### Paramètres  
 `value1`  
 Obligatoire.  Première valeur à tester.  
  
 `value2`  
 Obligatoire.  Seconde valeur à tester.  
  
## Valeur de retour  
 `true` si la valeur est identique ; sinon, `false`.  
  
## Notes  
 Contrairement à l'opérateur \=\=, `Object.is` ne force aucun type lors du test des valeurs.  
  
 La comparaison appliquée par `Object.is` est similaire à celle appliquée par l'opérateur \=\=\=, à ceci près qu'`Object.is` traite `Number.isNaN` comme la même valeur que `NaN`.  Il traite également \+0 et \-0 comme des valeurs différentes.  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]