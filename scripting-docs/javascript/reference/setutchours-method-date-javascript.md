---
title: "setUTCHours, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "setUTCHours (méthode)"
  - "temps UTC, définir"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setUTCHours, m&#233;thode (Date) (JavaScript)
Définit les heures représentées dans l'objet `Date` au format UTC \(Universal Coordinated Time\).  
  
## Syntaxe  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numHours`  
 Obligatoire.  Valeur numérique égale à celle des heures.  
  
 `numMin`  
 Facultatif.  Valeur numérique égale à celle des minutes.  Doit être spécifié si `numSec` ou `numMilli` est utilisé.  
  
 `numSec`  
 Facultatif.  Valeur numérique égale à celle des secondes.  Doit être spécifié si l'argument `numMilli` est utilisé.  
  
 `numMilli`  
 Facultatif.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument `numMin` n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode `getUTCMinutes`.  
  
 Pour définir la valeur des heures en heure locale, utilisez la méthode `setHours`.  
  
 Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 » et que la méthode **setUTCHours\(30\)** est appelée, la date devient « 6 Jan 1996 06:00:00.00 ».  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCHours`.  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getHours, méthode \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours, méthode \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours, méthode \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)