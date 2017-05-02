---
title: "getUTCHours, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "heures"
  - "UTC (heures), retour"
  - "getUTCHours (méthode)"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCHours, m&#233;thode (Date) (JavaScript)
Obtient la valeur d'heures dans un objet d' `Date` selon le temps UTC \(UTC\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne un entier compris entre 0 et 23 qui indique le nombre d'heures depuis minuit.  Zéro est retournée si le temps nécessaire avant 1h00 : 0h du matin.  Si un objet d' `Date` a été créé sans spécifier le temps par défaut, l'heure est 0 dans le temps l'heure UTC.  Cette période peut être différente de zéro dans d'autres fuseaux horaires.  
  
## Notes  
 Pour obtenir le nombre d'heures écoulées depuis minuit en heure locale, utilisez la méthode `getHours`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCHours`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getHours, méthode \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours, méthode \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours, méthode \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)