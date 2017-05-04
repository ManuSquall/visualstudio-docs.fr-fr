---
title: "Date.now, fonction (JavaScript) | Microsoft Docs"
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
  - "now (méthode)"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Date.now, fonction (JavaScript)
Obtient la date et l'heure actuelles.  
  
## Syntaxe  
  
```  
  
Date.now()  
```  
  
## Valeur de retour  
 Nombre de millisecondes écoulées entre le 1er janvier 1970 à minuit et la date et l'heure actuelles.  
  
## Notes  
 La [méthode getTime](../../javascript/reference/gettime-method-date-javascript.md) retourne le nombre de millisecondes écoulées entre le 1er janvier 1970 et une date spécifiée.  
  
 Pour plus d'informations sur le calcul du temps écoulé et la comparaison de dates, consultez [Calcul des dates et des heures \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `now`.  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## Configuration requise  
 Non prise en charge dans les versions installées antérieures à Internet Explorer 9.  Toutefois, elle n'est pas prise en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\).  Également pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Voir aussi  
 [getTime, méthode \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date, objet](../../javascript/reference/date-object-javascript.md)   
 [Calcul des dates et des heures \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Méthodes JavaScript](../../javascript/reference/javascript-methods.md)