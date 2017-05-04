---
title: "setMinutes, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "minutes"
  - "setMinutes (méthode)"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMinutes, m&#233;thode (Date) (JavaScript)
Définit les minutes, en heure locale, représentées dans l'objet **Date** .  
  
## Syntaxe  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 `numMinutes`  
 Obligatoire.  Valeur numérique égale à celle des minutes.  Doit être fournie si l'un des arguments suivants est utilisé.  
  
 *numSeconds*  
 Facultatif.  Valeur numérique égale à celle des secondes.  Doit être fourni si l'argument `numMilli` est utilisé.  
  
 `numMilli`  
 Facultatif.  Valeur numérique égale à celle des millisecondes.  
  
## Notes  
 Toutes les méthodes **set** acceptant des arguments facultatifs utilisent la valeur retournée par les méthodes **get** correspondantes lorsqu'aucun argument facultatif n'est spécifié.  Par exemple, si l'argument *numSeconds* n'est pas spécifié, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] utilise la valeur retournée par la méthode `getSeconds`.  
  
 Pour définir la valeur des minutes au format UTC \(Universal Coordinated Time\), utilisez la méthode `setUTCMinutes`.  
  
 Si la valeur d'un argument est un nombre supérieur à sa plage ou négatif, les autres valeurs stockées sont modifiées en conséquence.  Par exemple, si la date stockée est « 5 Jan 1996 00:00:00 » et que la méthode **setMinutes\(90\)** est appelée, la date est remplacée par « 5 Jan 1996 01:30:00 ». Les nombres négatifs ont un comportement similaire.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setMinutes`.  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMinutes, méthode \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes, méthode \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes, méthode \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)