---
title: "setSeconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds (méthode)"
  - "setSeconds (méthode)"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setSeconds, m&#233;thode (Date) (JavaScript)
Définit la valeur des secondes de l'objet `Date` en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 *numSeconds*  
 Obligatoire.  Valeur numérique égale à celle des secondes.  
  
 `numMilli`  
 Facultatif.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument `numMilli` n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode **getMilliseconds**.  
  
 Pour définir la valeur des secondes au format UTC \(Universal Time Coordinated\), utilisez la méthode `setUTCSeconds`.  
  
 Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 00:00:00 » et que la méthode **setSeconds\(150\)** est appelée, la date est remplacée par « 5 Jan 1996 00:02:30 ».  
  
 La méthode `setHours` peut être utilisée pour définir les heures, minutes, secondes et millisecondes.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setSeconds`.  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getSeconds, méthode \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds, méthode \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds, méthode \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)