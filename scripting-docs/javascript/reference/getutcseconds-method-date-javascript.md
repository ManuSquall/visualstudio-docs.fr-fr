---
title: "getUTCSeconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC (heures), retour"
  - "seconds (méthode)"
  - "getUTCSeconds (méthode)"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCSeconds, m&#233;thode (Date) (JavaScript)
Obtient les secondes d'un objet d' `Date` selon le temps UTC \(UTC\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne un entier compris entre 0 et 59.  Zéro est retourné lorsque le temps est moins de seconde dans la minute actuelle.  Si un objet d' `Date` a été créé sans spécifier le temps, par défaut la valeur des secondes à l'heure UTC est 0.  
  
## Notes  
 Pour obtenir le nombre de secondes exprimé en heure locale, utilisez la méthode `getSeconds`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getSeconds, méthode \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds, méthode \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds, méthode \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)