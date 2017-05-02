---
title: "setUTCMonth, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "Month (méthode)"
  - "setUTCMonth (méthode)"
  - "dates UTC, définir"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMonth, m&#233;thode (Date) (JavaScript)
Définit le mois dans l'objet `Date` selon le temps universel.  
  
## Syntaxe  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numMonth`  
 Obligatoire.  Valeur numérique égale au mois.  La valeur pour janvier est 0 et les valeurs des autres mois suivent celle\-ci de manière consécutive.  
  
 `dateVal`  
 Facultatif.  Valeur numérique représentant le jour du mois.  Si elle n'est pas fournie, la valeur employée est celle qui est retournée par un appel à la méthode `getUTCDate`.  
  
## Notes  
 Pour définir le mois en heure locale, utilisez la méthode `setMonth`.  
  
 Si la valeur de l'argument `numMonth` est supérieure à 11 \(janvier correspondant au mois 0\), ou si elle est négative, l'année stockée est incrémentée ou décrémentée en conséquence.  Par exemple, si la date stockée est « 5 jan 1996 00:00:00 » et que la méthode **setUTCMonth\(14\)** est appelée, la date est remplacée par « 5 mar 1997 00:00:00:00 ».  
  
 La méthode **setUTCFullYear** est utilisée pour définir l'année, le mois et le jour du mois.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCMonth`.  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMonth, méthode \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth, méthode \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth, méthode \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)