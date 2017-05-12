---
title: "setHours, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, définir"
  - "heures"
  - "setHours (méthode)"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setHours, m&#233;thode (Date) (JavaScript)
Définit l'heure, en heure locale, représentée dans l'objet `Date`.  
  
## Syntaxe  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numHours`  
 Obligatoire.  Valeur numérique égale à celle des heures.  
  
 `numMin`  
 Facultatif.  Valeur numérique égale à celle des minutes.  Doit être fournie si l'un des arguments suivants est utilisé.  
  
 `numSec`  
 Facultatif.  Valeur numérique égale à celle des secondes.  Doit être spécifié si l'argument suivant est utilisé.  
  
 `numMilli`  
 Facultatif.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument `numMinutes` n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode `getMinutes`.  
  
 Pour définir la valeur des heures au format UTC \(Universal Coordinated Time\), utilisez la méthode `setUTCHours`.  
  
 Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 00:00:00 » et que la méthode **setHours\(30\)** est appelée, la date devient « 6 Jan 1996 06:00:00 ». Les nombres négatifs ont un comportement similaire.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setHours`.  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getHours, méthode \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours, méthode \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours, méthode \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)