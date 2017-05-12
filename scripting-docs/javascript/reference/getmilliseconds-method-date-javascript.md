---
title: "getMilliseconds, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "millisecondes"
  - "getMilliseconds (méthode)"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMilliseconds, m&#233;thode (Date) (JavaScript)
Obtient les millisecondes d'une date en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne les millisecondes d'une date.  La valeur peut varier de 0 à 999.  Si une date a été construite sans spécifier les millisecondes, la valeur retournée est égale à 0.  
  
## Notes  
 Pour obtenir le nombre de millisecondes au format UTC \(Universal Coordinated Time\), utilisez la méthode `getUTCMilliseconds`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **getMilliseconds**.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCMilliseconds, méthode \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds, méthode \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds, méthode \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)