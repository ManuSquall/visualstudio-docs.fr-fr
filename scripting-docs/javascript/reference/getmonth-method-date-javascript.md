---
title: "getMonth, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "dates, valeur du mois"
  - "Month (méthode)"
  - "GetMonth (méthode)"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getMonth, m&#233;thode (Date) (JavaScript)
Obtient le mois en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getMonth()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 La méthode `getMonth` retourne un entier compris entre 0 \(janvier\) et 11 \(décembre\).  Pour un `Date` construit avec « 5 Jan 1996 », `getMonth` retourne 0.  
  
## Notes  
 Pour obtenir le mois au format UTC \(Universal Coordinated Time\), utilisez la méthode `getUTCMonth`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getMonth`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCMonth, méthode \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth, méthode \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth, méthode \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)