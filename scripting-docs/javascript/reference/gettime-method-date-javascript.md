---
title: "getTime, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTime (méthode)"
  - "time (méthode)"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getTime, m&#233;thode (Date) (JavaScript)
Obtient la valeur de temps en millisecondes.  
  
## Syntaxe  
  
```  
  
dateObj.getTime()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne le nombre de millisecondes entre le 1er janvier 1970 à minuit et la valeur d'heure dans l'objet `Date`.  La plage de dates est approximativement de 285 616 années avant et après le 1 er janvier 1970, minuit.  Les nombres négatifs indiquent des dates antérieures à 1970.  
  
## Notes  
 Lors de l'exécution de plusieurs calculs de date et d'heure, vous pouvez définir des variables égales au nombre de millisecondes dans un jour, une heure ou une minute.  Par exemple :  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Pour plus d'informations sur l'utilisation de la méthode [Calcul des dates et des heures \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md), consultez `getTime`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getTime`.  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [setTime, méthode \(Date\)](../../javascript/reference/settime-method-date-javascript.md)