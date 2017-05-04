---
title: "setMilliseconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "millisecondes"
  - "setMilliseconds (méthode)"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMilliseconds, m&#233;thode (Date) (JavaScript)
Définit la valeur des millisecondes de l'objet `Date` en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numMilli`  
 Obligatoire.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Pour définir les millisecondes selon le temps universel \(UTC, Universal Time Coordinated\), utilisez la méthode `setUTCMilliseconds`.  
  
 Si la valeur de l'argument `numMilli` est supérieure à 999 ou si elle est négative, le nombre de secondes stocké est modifié en conséquence, de même que les minutes, les heures et d'autres valeurs le cas échéant.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setMilliseconds`.  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMilliseconds, méthode \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds, méthode \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds, méthode \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)