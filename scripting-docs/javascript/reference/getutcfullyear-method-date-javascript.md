---
title: "getUTCFullYear, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear (méthode)"
  - "Date (objet)"
  - "UTCFullYear (méthode)"
  - "dates, UTC"
  - "UTC (dates), retourner"
  - "Full Year (méthode)"
  - "UTC (dates), obtenir"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCFullYear, m&#233;thode (Date) (JavaScript)
Obtient l'année au format UTC \(Universal Coordinated Time\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne l'année, sous la forme d'un nombre de quatre chiffres.  Les années spécifiées sous la forme de deux chiffres dans le constructeur `Date` ou dans `setFullYear` ont lieu au 20ème siècle, soit « 5\/14\/12 », `getUTCFullYear` retourne « 1912 ».  
  
## Notes  
 Pour obtenir l'année en heure locale, utilisez la méthode `getFullYear`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCFullYear`.  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getFullYear, méthode \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear, méthode \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)