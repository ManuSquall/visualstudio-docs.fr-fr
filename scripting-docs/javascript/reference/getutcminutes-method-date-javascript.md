---
title: "getUTCMinutes, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "minutes"
  - "UTC (heures), retour"
  - "getUTCMinutes (méthode)"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMinutes, m&#233;thode (Date) (JavaScript)
Obtient les minutes d'un objet d' `Date` selon le temps UTC \(UTC\).  
  
## Syntaxe  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### Paramètres  
 La référence requise pour `dateObj` est un objet d' `Date` .  
  
## Valeur de retour  
 Retourne un entier compris entre 0 et 59.  Zéro est retourné le temps est moins une minute après l'heure.  Si un objet d' `Date` a été créé sans spécifier le temps, par défaut la valeur des minutes de l'heure UTC est 0.  Toutefois, dans d'autres fuseaux horaires elle peut être différente.  
  
## Notes  
 Pour obtenir le nombre de minutes exprimé en heure locale, utilisez la méthode `getMinutes`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `getUTCMinutes`.  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getMinutes, méthode \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes, méthode \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes, méthode \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)