---
title: "toISOString, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "toISOString (méthode) (JavaScript)"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# toISOString, m&#233;thode (Date) (JavaScript)
Retourne une date sous forme de valeur de chaîne au format ISO.  
  
## Syntaxe  
  
```javascript  
  
objDate.toISOString()  
```  
  
## Valeur de retour  
 Représentation sous forme de chaîne de la date au format ISO \(International Organization for Standardization\).  
  
## Exceptions  
 Si `objDate` ne contient pas de date valide, une exception `RangeError` est levée.  
  
## Notes  
 Le format ISO est une simplification du format ISO 8601.  Pour plus d'informations, consultez [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md).  
  
 Le fuseau horaire est toujours UTC, désigné par le suffixe Z dans la sortie.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `toISOString`.  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Date, objet](../../javascript/reference/date-object-javascript.md)   
 [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md)