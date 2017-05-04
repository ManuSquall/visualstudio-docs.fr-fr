---
title: "toTimeString, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString (méthode)"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toTimeString, m&#233;thode (Date) (JavaScript)
Retourne une valeur horaire sous forme de valeur de chaîne.  
  
## Syntaxe  
  
```  
  
objDate. toTimeString( )  
```  
  
## Notes  
 La référence `objDate` requise est un objet `Date`.  
  
 La méthode `toTimeString` retourne une valeur de chaîne contenant l'heure du fuseau horaire actuel.  
  
## Exemple  
 Dans l'exemple suivant, l'heure est définie à 2 000 millisecondes après minuit, le 1er janvier 1970 UTC, puis elle est écrite.  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Voir aussi  
 [toDateString, méthode \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString, méthode \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)