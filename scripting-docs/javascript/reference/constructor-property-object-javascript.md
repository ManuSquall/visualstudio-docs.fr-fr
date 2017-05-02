---
title: "constructor, propri&#233;t&#233; (Object) (JavaScript) | Microsoft Docs"
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
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor (propriété)"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# constructor, propri&#233;t&#233; (Object) (JavaScript)
Spécifie la fonction qui crée un objet.  
  
## Syntaxe  
  
```  
  
object.constructor  
```  
  
## Notes  
 L'`object` requis est le nom d'un objet ou d'une fonction.  
  
 La propriété `constructor` est un membre du prototype de chaque objet qui en possède un.  Cela inclut tous les objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinsèques à l'exception des objets `Global` et `Math`.  La propriété `constructor` contient une référence à la fonction qui crée les instances d'un objet donné.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété constructor.  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [prototype, propriété \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)