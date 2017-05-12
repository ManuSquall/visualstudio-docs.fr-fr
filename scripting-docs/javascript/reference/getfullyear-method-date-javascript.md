---
title: "getFullYear, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, retourner l’année"
  - "Date (objet)"
  - "getFullYear (méthode)"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# getFullYear, m&#233;thode (Date) (JavaScript)
Obtient l'année en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getFullYear()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Année, sous la forme d'un nombre de quatre chiffres.  Par exemple, l'année 1976 est retournée sous la forme « 1976 ».  Les années spécifiées sous la forme de deux chiffres dans le constructeur `Date` ou dans `setFullYear` ont lieu au 20ème siècle, soit « 5\/14\/12 », `getFullYear` retourne « 1912 ».  
  
## Notes  
 Pour obtenir l'année selon le temps universel \(UTC, Universal Time Coordinated\), utilisez la méthode `getUTCFullYear`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **getFullYear**.  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCFullYear, méthode \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear, méthode \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)