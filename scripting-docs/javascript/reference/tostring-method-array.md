---
title: "toString, m&#233;thode (Array) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toString, m&#233;thode (Array)
Retourne une représentation sous forme de chaîne d'un tableau.  
  
## Syntaxe  
  
```  
  
array.toString()  
```  
  
## Paramètres  
 `array`  
 Obligatoire.  Tableau à représenter en tant que chaîne.  
  
## Valeur de retour  
 Représentation sous forme de chaîne du tableau.  
  
## Notes  
 Les éléments d'un objet `Array` sont convertis en chaînes.  Les chaînes résultantes sont concaténées et séparées par des virgules.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode **toString** avec un tableau.  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]