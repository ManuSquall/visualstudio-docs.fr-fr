---
title: "setUTCMinutes, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "minutes"
  - "setUTCMinutes (méthode)"
  - "temps UTC, définir"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMinutes, m&#233;thode (Date) (JavaScript)
Définit les minutes représentées dans l'objet `Date` au format UTC \(Universal Coordinated Time\).  
  
## Syntaxe  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numMinutes`  
 Obligatoire.  Valeur numérique égale à celle des minutes.  Doit être fournie si l'un des arguments suivants est utilisé.  
  
 *numSeconds*  
 Facultatif.  Valeur numérique égale à celle des secondes.  Doit être fournie si l'argument `numMilli` est spécifié.  
  
 `numMilli`  
 Facultatif.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument *numSeconds* n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode `getUTCSeconds`.  
  
 Pour modifier les minutes en heure locale, utilisez la méthode `setMinutes`.  
  
 Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 00:00:00.00 » et que la méthode **setUTCMinutes\(70\)** est appelée, la date est remplacée par « 5 Jan 1996 01:10:00.00 ».  
  
 La méthode **setUTCHours** peut être utilisée pour définir les heures, minutes, secondes et millisecondes.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCMinutes` :  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMinutes, méthode \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes, méthode \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes, méthode \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)