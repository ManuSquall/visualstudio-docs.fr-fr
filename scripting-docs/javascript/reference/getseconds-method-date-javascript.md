---
title: "getSeconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds (méthode)"
  - "GetSeconds (méthode)"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getSeconds, m&#233;thode (Date) (JavaScript)
Obtient les secondes d'un objet d' `Date` , en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getSeconds()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne un entier compris entre 0 et 59.  Zéro est retourné lorsque le temps est moins de seconde dans la minute actuelle.  Si un objet d' `Date` a été créé sans spécifier le temps, par défaut la valeur de est 0 secondes.  
  
## Notes  
 Pour obtenir la valeur des secondes à l'heure UTC \(UTC\), utilisez la méthode d' `getUTCSeconds` .  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getSeconds`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **s'applique à**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCSeconds, méthode \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds, méthode \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds, méthode \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)