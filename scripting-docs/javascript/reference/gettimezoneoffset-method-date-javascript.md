---
title: "getTimezoneOffset, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset (méthode)"
  - "fuseaux horaires (Visual Studio)"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getTimezoneOffset, m&#233;thode (Date) (JavaScript)
Obtient la différence en minutes entre l'heure de l'ordinateur local et l'heure universelle coordonnée \(UTC, Universal Coordinated Time\).  
  
## Syntaxe  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne le nombre de minutes entre l'heure de l'ordinateur actuel \(l'ordinateur client ou, si cette méthode est appelée à partir d'un script serveur, l'ordinateur serveur\) et l'heure UTC.  La valeur est positive si l'heure locale de l'ordinateur actuel est après l'heure UTC \(zone Pacifique des États\-Unis, par exemple\), et négative si l'heure locale de l'ordinateur actuel est avant l'heure UTC \(Japon, par exemple\).  Si un serveur à New York City est contacté par un client à Los Angeles le 1er décembre, la méthode `getTimezoneOffset` retourne 480 si elle est exécutée sur le client, ou 300 si elle est exécutée sur le serveur.  
  
## Notes  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getTimezoneOffset`.  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getTime, méthode \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)