---
title: "setDate, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate (méthode)"
  - "dates, définition"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setDate, m&#233;thode (Date) (JavaScript)
Définit la valeur numérique de jour\-de\-le\- mois de l'objet d' `Date` en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numDate`  
 Obligatoire.  Valeur numérique correspondant au jour du mois.  
  
## Notes  
 Pour définir la valeur de jour\-de\-le\- mois selon le temps UTC \(UTC\), utilisez la méthode d' `setUTCDate` .  
  
 Si la valeur d' `numDate` est supérieure au nombre de jours du mois, la date comment annuler des vers vers la fin du mois et\/ou d'année.  Par exemple, si la date enregistrée est le le 5 janvier 1996 et `setDate(32)` est appelé, la date devient le 1er février 1996.  Si `numDate` est un nombre négatif, la date comment annuler vers un mois et\/ou à une année précédemment.  Par exemple, si la date enregistrée est le le 5 janvier 1996 et `setDate(-32)` est appelé, la date devient le 29 novembre 1995.  
  
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md) peut être utilisé pour définir l'année, le mois, le jour du mois.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setDate`.  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getDate, méthode \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth, méthode \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate, méthode \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)