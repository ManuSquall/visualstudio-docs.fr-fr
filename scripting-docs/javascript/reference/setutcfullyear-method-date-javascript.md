---
title: "setUTCFullYear, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "dates, UTC"
  - "setUTCFullYear (méthode)"
  - "dates UTC, définir"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCFullYear, m&#233;thode (Date) (JavaScript)
Définit la valeur de l'année de l'objet `Date` en heure UTC.  
  
## Syntaxe  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numYear`  
 Obligatoire.  Valeur numérique égale à l'année.  
  
 `numMonth`  
 Facultatif.  Valeur numérique égale au mois.  La valeur pour janvier est 0 et les valeurs des autres mois suivent celle\-ci de manière consécutive.  Doit être fournie si l'argument *numDate* est spécifié.  
  
 *numDate*  
 Facultatif.  Valeur numérique égale au jour du mois.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument `numMonth` n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode `getUTCMonth`.  
  
 En outre, si la valeur d'un argument est supérieure à la plage de ce dernier ou si elle est négative, les autres valeurs stockées sont modifiées en conséquence.  
  
 Pour définir l'année en heure locale, utilisez la méthode `setFullYear`.  
  
 La plage des années prise en charge dans l'objet `Date` couvre environ 285 616 années avant ou après 1970.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setUTCFullYear`.  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getFullYear, méthode \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear, méthode \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear, méthode \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)