---
title: "setUTCDate, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, définir"
  - "dates, UTC"
  - "setUTCDate (méthode)"
  - "dates UTC, définir"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# setUTCDate, m&#233;thode (Date) (JavaScript)
Définit le numéro du jour du mois, exprimé selon le temps universel coordonné \(UTC, Universal Coordinated Time\), dans l'objet `Date`.  
  
## Syntaxe  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 *numDate*  
 Obligatoire.  Valeur numérique égale au jour du mois.  
  
## Notes  
 Pour définir le jour du mois exprimé en heure locale, utilisez la méthode `setDate`.  
  
 Si la valeur de *numDate* est supérieure au nombre de jours du mois stocké dans l'objet **Date**, ou si cette valeur est négative, la date définie sera égale à la date numérique \(*numDate*\) moins le nombre de jours compris dans le mois stocké.  Par exemple, si la date stockée est le 5 janvier 1996, et que la méthode **setUTCDate\(32\)** est appelée, la date est remplacée par le 1er février 1996.  Les nombres négatifs ont un comportement similaire.  
  
 La méthode **setUTCFullYear** est utilisée pour définir l'année, le mois et le jour du mois.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCDate`.  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getDate, méthode \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate, méthode \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate, méthode \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)