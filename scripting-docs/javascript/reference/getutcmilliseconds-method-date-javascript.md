---
title: "getUTCMilliseconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "millisecondes"
  - "UTC (heures), retour"
  - "getUTCMilliseconds (méthode)"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMilliseconds, m&#233;thode (Date) (JavaScript)
Obtient les millisecondes d'un objet d' `Date` selon le temps UTC \(UTC\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne une valeur de millisecondes qui peut varier de 0\-999.  
  
## Notes  
 Pour obtenir le nombre de millisecondes dans le temps l'heure locale, utilisez la méthode d' `getMilliseconds` .  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCMilliseconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMilliseconds, méthode \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds, méthode \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds, méthode \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)