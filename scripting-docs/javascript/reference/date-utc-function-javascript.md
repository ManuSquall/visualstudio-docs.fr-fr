---
title: "Date.UTC, fonction (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC (fonction) (JavaScript)"
  - "UTC (dates), retourner"
  - "Date.UTC (fonction) (JavaScript)"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Date.UTC, fonction (JavaScript)
Retourne le nombre de millisecondes entre le 1er janvier 1970 à minuit, selon le temps universel \(UTC, Universal Time Coordinated\) ou l'heure de Greenwich \(GMT, Greenwich Mean Time\), et la date spécifiée.  
  
## Syntaxe  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Paramètres  
 `year`  
 Obligatoire.  La désignation complète de l'année est obligatoire pour permettre de distinguer les dates d'un siècle à un autre.  Si l'élément `year` utilisé est compris entre 0 et 99, l'élément `year` est supposé correspondre à 1900 \+ `year`.  
  
 `month`  
 Obligatoire.  Le mois, représenté par un entier compris entre 0 et 11 \(janvier à décembre\).  
  
 `day`  
 Obligatoire.  Le jour de la date, représentée par un entier compris entre 1 et 31.  
  
 `hours`  
 Facultatif.  Doit être indiqué si l'argument `minutes` est spécifié.  Entier compris entre 0 et 23 \(de minuit à 23 heures\) indiquant l'heure.  
  
 `minutes`  
 Facultatif.  Doit être indiqué si l'argument `seconds` est spécifié.  Entier compris entre 0 et 59 indiquant les minutes.  
  
 `seconds`  
 Facultatif.  Doit être indiqué si l'argument `milliseconds` est spécifié.  Entier compris entre 0 et 59 indiquant les secondes.  
  
 `ms`  
 Facultatif.  Entier compris entre 0 et 999 indiquant les millisecondes.  
  
## Notes  
 La fonction `Date.UTC` retourne le nombre de millisecondes entre le 1er janvier 1970 à minuit \(temps universel\) et la date fournie.  La valeur de retour peut être utilisée dans la méthode `setTime` et dans le constructeur de l'objet `Date`.  Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si vous spécifiez 150 secondes, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit ce nombre en deux minutes et trente secondes.  
  
 La différence entre la fonction `Date.UTC` et le constructeur de l'objet `Date` qui accepte une date est que la fonction `Date.UTC` se base sur le temps universel alors que le constructeur de l'objet `Date` fait référence à l'heure locale.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Date.UTC`.  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [setTime, méthode \(Date\)](../../javascript/reference/settime-method-date-javascript.md)