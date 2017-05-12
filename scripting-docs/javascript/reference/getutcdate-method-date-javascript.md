---
title: "getUTCDate, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "dates, UTC"
  - "UTC (dates), retour"
  - "getUTCDate (méthode)"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getUTCDate, m&#233;thode (Date) (JavaScript)
Obtient le jour du mois au format UTC \(Universal Coordinated Time\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne un entier compris entre 1 et 31 qui représente le jour du mois.  
  
## Notes  
 Pour obtenir le jour du mois exprimé en heure locale, utilisez la méthode `getDate`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCDate`.  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getDate, méthode \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate, méthode \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate, méthode \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)