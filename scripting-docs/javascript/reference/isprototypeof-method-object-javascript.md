---
title: "isPrototypeOf, m&#233;thode (Object) (JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf (méthode)"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# isPrototypeOf, m&#233;thode (Object) (JavaScript)
Détermine si l'objet existe dans la chaîne prototype d'un autre objet.  
  
## Syntaxe  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## Paramètres  
 `prototype`  
 Obligatoire.  Un prototype d'objet.  
  
 `object`  
 Obligatoire.  Autre objet dont la chaîne prototype est à vérifier.  
  
## Notes  
 La méthode `isPrototypeOf` retourne la valeur `true` si `object` a `prototype` dans sa chaîne prototype.  La chaîne prototype est utilisée pour partager les fonctionnalités entre des instances d'un même type d'objet.  La méthode `isPrototypeOf` retourne `false` si `object` n'est pas un objet ou si `prototype` n'apparaît pas dans la chaîne prototype d'`object`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `isPrototypeOf`.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [prototype, propriété \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)