---
title: "setTime, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime (méthode)"
  - "time (méthode)"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# setTime, m&#233;thode (Date) (JavaScript)
Définit la date et l'heure dans l'objet `Date`.  
  
## Syntaxe  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## Paramètres  
 `dateObj`  
 Obligatoire.  Tout objet `Date`.  
  
 *millisecondes*  
 Obligatoire.  Valeur numérique représentant le nombre de millisecondes écoulées depuis le 1er janvier 1970 à minuit, en temps universel.  
  
## Notes  
 Si les *millisecondes* sont négatives, cela indique une date avant 1970.  La plage des dates disponibles couvre environ 285 616 années avant et après 1970.  
  
 La définition de la date et de l'heure avec la méthode `setTime` est indépendante du fuseau horaire.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `setTime`.  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getTime, méthode \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)