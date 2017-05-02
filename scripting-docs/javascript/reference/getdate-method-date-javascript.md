---
title: "getDate, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "dates, retour du jour du mois"
  - "getDate (méthode)"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# getDate, m&#233;thode (Date) (JavaScript)
Obtient le numéro du jour du mois en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getDate()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Entier compris entre 1 et 31 qui représente le jour du mois.  
  
## Notes  
 Pour obtenir le jour du mois exprimé en temps universel \(UTC, Universal Coordinated Time\), utilisez la méthode `getUTCDate`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getDate`.  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCDate, méthode \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate, méthode \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate, méthode \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)