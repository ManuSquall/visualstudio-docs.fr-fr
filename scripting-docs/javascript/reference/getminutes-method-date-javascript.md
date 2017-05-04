---
title: "getMinutes, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes (méthode)"
  - "minutes (méthode)"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMinutes, m&#233;thode (Date) (JavaScript)
Obtient les minutes d'un objet `Date` en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj.getMinutes()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Retourne un entier compris entre 0 et 59.  La valeur zéro est retournée ; le temps est inférieur à une minute après l'heure.  Si un objet `Date` a été créé sans spécifier l'heure, par défaut la valeur minute est égale à 0.  
  
## Notes  
 Pour obtenir la valeur des minutes au format UTC \(Universal Coordinated Time\), utilisez la méthode `getUTCMinutes`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCMinutes, méthode \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes, méthode \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes, méthode \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)