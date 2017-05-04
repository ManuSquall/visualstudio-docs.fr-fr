---
title: "setUTCMilliseconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "millisecondes"
  - "setUTCMilliseconds (méthode)"
  - "temps UTC, définir"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMilliseconds, m&#233;thode (Date) (JavaScript)
Définit la valeur de millisecondes de l'objet `Date` en heure UTC.  
  
## Syntaxe  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numMilli`  
 Obligatoire.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Pour définir les millisecondes en heure locale, utilisez la méthode `setMilliseconds`.  
  
 Si la valeur de l'argument `numMilli` est supérieure à 999 ou si elle est négative, le nombre de secondes stocké est modifié en conséquence, de même que les minutes, les heures et d'autres valeurs le cas échéant.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCMilliseconds`.  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMilliseconds, méthode \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds, méthode \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds, méthode \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)