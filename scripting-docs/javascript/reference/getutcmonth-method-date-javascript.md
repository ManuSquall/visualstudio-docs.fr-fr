---
title: "getUTCMonth, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "UTC (dates), retourner"
  - "Month (méthode)"
  - "getUTCMonth (méthode)"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMonth, m&#233;thode (Date) (JavaScript)
Obtient le mois d'un objet d' `Date` selon le temps UTC \(UTC\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne un entier compris entre 0 \(janvier\) et 11 \(décembre\).  
  
## Notes  
 Pour obtenir le mois exprimé en heure locale, utilisez la méthode **getMonth**.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCMonth`.  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMonth, méthode \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth, méthode \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth, méthode \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)