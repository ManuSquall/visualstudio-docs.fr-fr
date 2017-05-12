---
title: "getUTCDay, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "dates, UTC"
  - "UTC (dates), retour"
  - "getUTCDay (méthode)"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getUTCDay, m&#233;thode (Date) (JavaScript)
Obtient le jour de la semaine au format UTC \(Universal Coordinated Time\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne un entier compris entre 0 \(dimanche\) et 6 \(samedi\) qui représente le jour de la semaine.  
  
## Notes  
 Pour obtenir le jour de la semaine en heure locale, utilisez la méthode `getDate`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCDay`.  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getDay, méthode \(Date\)](../../javascript/reference/getday-method-date-javascript.md)