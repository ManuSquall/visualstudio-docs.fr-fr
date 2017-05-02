---
title: "setFullYear, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year (méthode)"
  - "setFullYear (méthode)"
  - "dates, définition"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setFullYear, m&#233;thode (Date) (JavaScript)
Définit l'année de l'objet d' `Date` en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numYear`  
 Obligatoire.  Une valeur numérique pendant l'année.  
  
 `numMonth`  
 Facultatif.  Une valeur numérique de base zéro du mois \(0 à janvier 11, pour décembre\).  Doit être spécifié si `numDate` est spécifié.  
  
 `numDate`  
 Facultatif.  Une valeur numérique égale pour le jour du mois.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'un argument facultatif n'est pas spécifié.  Par exemple, si l'argument d' `numMonth` est facultative, mais pas spécifié, utilise d' [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que la valeur a retournées par la méthode de **getMonth** .  
  
 En outre, si la valeur d'un argument est supérieure à sa plage de calendrier ou est négative, les roulettes de date effectuent le suivi ou arrière selon le cas.  
  
 Pour définir l'année avec le temps UTC \(UTC\), utilisez la méthode d' `setUTCFullYear` .  
  
 La plage des années charge dans l'objet de date est d'environ 285.616 ans avant et après 1970.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode `setFullYear` :  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getFullYear, méthode \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear, méthode \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)