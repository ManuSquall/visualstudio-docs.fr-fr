---
title: "getDay, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay (méthode)"
  - "Date (objet)"
  - "dates, retourner le jour de la semaine"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# getDay, m&#233;thode (Date) (JavaScript)
Obtient le jour de la semaine en heure locale.  
  
## Syntaxe  
  
```  
  
dateObj. getDay()   
```  
  
#### Paramètres  
 La référence `dateObj` requise est un objet `Date`.  
  
## Valeur de retour  
 Entier compris entre 0 et 6 qui représente le jour de la semaine \(dimanche est égal à 0, samedi à 6\).  
  
## Notes  
 Pour obtenir le jour au format UTC \(Universal Coordinated Time\), utilisez la méthode `getUTCDay`.  
  
 L'exemple suivant illustre l'utilisation de la méthode `getDay`.  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getUTCDay, méthode \(Date\)](../../javascript/reference/getutcday-method-date-javascript.md)