---
title: "toUTCString, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString (méthode)"
  - "dates UTC, convertir en chaînes"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toUTCString, m&#233;thode (Date) (JavaScript)
Retourne une date convertie en chaîne à l'heure UTC.  
  
## Syntaxe  
  
```  
  
dateObj.toUTCString()   
```  
  
## Notes  
 La référence `dateObj` requise est un objet `Date`.  
  
 La méthode `toUTCString` retourne un objet `String` contenant la date exprimée selon le temps universel \(UTC\), dans un format facile à lire.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toUTCString`.  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [toGMTString, méthode \(Date\)](../../javascript/reference/togmtstring-method-date-javascript.md)