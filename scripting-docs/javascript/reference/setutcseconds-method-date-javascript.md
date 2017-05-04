---
title: "setUTCSeconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "seconds (méthode)"
  - "setUTCSeconds (méthode)"
  - "temps UTC, définir"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCSeconds, m&#233;thode (Date) (JavaScript)
Définit la valeur des secondes de l'objet `Date` en heure UTC.  
  
## Syntaxe  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 *numSeconds*  
 Obligatoire.  Valeur numérique égale à celle des secondes.  
  
 `numMilli`  
 Facultatif.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument `numMilli` n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode `getUTCMilliseconds`.  
  
 Pour définir les secondes en heure locale, utilisez la méthode `setSeconds`.  
  
 Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 » et que la méthode **setSeconds\(150\)** est appelée, la date est remplacée par « 5 Jan 1996 00:02:30.00 ».  
  
 La méthode **setUTCHours** peut être utilisée pour définir les heures, minutes, secondes et millisecondes.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCSeconds`.  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getSeconds, méthode \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds, méthode \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds, méthode \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)