---
title: "valueOf, m&#233;thode (Date) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# valueOf, m&#233;thode (Date)
Retourne la valeur horaire stockée, exprimée en millisecondes écoulées depuis le 1er janvier 1970 à minuit \(temps universel\).  
  
## Syntaxe  
  
```  
  
date.valueOf()  
```  
  
#### Paramètres  
 L'objet `date` est une instance d'une date.  
  
## Valeur de retour  
 Valeur horaire stockée, exprimée en millisecondes écoulées depuis le 1er janvier 1970 à minuit \(temps universel\).  Il s'agit de la même valeur que `getTime`.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode `valueOf` avec une date.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]