---
title: "getHours, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "GetHours (méthode)"
  - "Hours (méthode)"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getHours, m&#233;thode (Date) (JavaScript)
Obtient les heures d'une date, en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getHours()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Valeur entière entre 0 et 23 qui indique le nombre d'heures écoulées depuis minuit.  La valeur zéro est retournée si l'heure est antérieure à 01:00:00.  Si un objet `Date` a été créé sans spécifier l'heure, par défaut la valeur des heures est égale à 0.  
  
## Notes  
 Pour obtenir les heures au format UTC \(Universal Coordinated Time\), utilisez la méthode `getUTCHours`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCHours, méthode \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours, méthode \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours, méthode \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)