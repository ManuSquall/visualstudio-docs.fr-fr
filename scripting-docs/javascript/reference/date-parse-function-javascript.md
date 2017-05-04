---
title: "Date.parse, fonction (JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse (fonction) (JavaScript)"
  - "parse (fonction) (JavaScript)"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Date.parse, fonction (JavaScript)
Analyse une chaîne contenant une date et retourne le nombre de millisecondes entre cette date et le 1er janvier 1970 à minuit.  
  
## Syntaxe  
  
```  
Date.parse(dateVal)   
```  
  
## Notes  
 L'argument `dateVal` requis est une chaîne contenant une date ou une valeur VT\_DATE extraite d'un objet ActiveX ou d'un autre objet.  Pour plus d'informations sur les chaînes de date que la fonction `Date.parse` peut analyser, consultez [Chaînes de date et heure](../../javascript/date-and-time-strings-javascript.md).  
  
 La fonction `Date.parse` retourne une valeur entière représentant le nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit et la date fournie dans `dateVal`.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `Date.parse` :  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## Exemple  
 L'exemple suivant retourne la différence entre la date fournie et celle du 1\/1\/1970.  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [getDate, méthode \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)