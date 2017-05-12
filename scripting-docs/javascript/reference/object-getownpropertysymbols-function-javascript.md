---
title: "Object.getOwnPropertySymbols, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.getOwnPropertySymbols, fonction (JavaScript)
Retourne les symboles de propriété personnels d'un objet.  Ces symboles sont ceux qui sont définis directement sur cet objet et non hérités du prototype de l'objet.  
  
## Syntaxe  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### Paramètres  
 `object`  
 Obligatoire.  Objet qui contient les symboles personnels.  
  
## Valeur de retour  
 Tableau qui contient les symboles personnels de l'objet.  
  
## Notes  
 Vous devez utiliser `Object.getOwnPropertySymbols` pour obtenir les symboles de propriété d'un objet.  `Object.getOwnPropertyNames` ne retourne pas les symboles de propriété.  
  
## Exemple  
 L'exemple de code suivant montre comment obtenir les symboles de propriété d'un objet.  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]