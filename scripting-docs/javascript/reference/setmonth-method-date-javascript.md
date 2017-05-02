---
title: "setMonth, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month (méthode)"
  - "setMonth (méthode)"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setMonth, m&#233;thode (Date) (JavaScript)
Définit le mois, en heure locale, représenté dans un objet `Date`.  
  
## Syntaxe  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numMonth`  
 Obligatoire.  Valeur numérique égale au mois.  La valeur pour janvier est 0 et les valeurs des autres mois suivent celle\-ci de manière consécutive.  
  
 `dateVal`  
 Facultatif.  Valeur numérique représentant le jour du mois.  Si cette valeur n'est pas fournie, la valeur employée est celle qui est retournée par un appel à la méthode `getDate`.  
  
## Notes  
 Pour définir la valeur du mois au format UTC \(Universal Coordinated Time\), utilisez la méthode `setUTCMonth`.  
  
 Si la valeur de l'argument `numMonth` est supérieure à 11 \(janvier correspondant au mois 0\), ou si elle est négative, l'année stockée est modifiée en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 » et que la méthode **setMonth\(14\)** est appelée, la date est remplacée par « 5 Mar 1997 ».  
  
 La méthode **setFullYear** peut être utilisée pour définir l'année, le mois et le jour du mois.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setMonth`.  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMonth, méthode \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth, méthode \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth, méthode \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)