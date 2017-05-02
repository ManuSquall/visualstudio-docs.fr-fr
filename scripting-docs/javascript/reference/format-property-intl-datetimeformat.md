---
title: "format, propri&#233;t&#233; (Intl.DateTimeFormat) | Microsoft Docs"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format, propri&#233;t&#233; (Intl.DateTimeFormat)
Retourne une fonction qui met une date en forme spécifique aux paramètres régionaux à l'aide des paramètres du formateur de date\/heure spécifiés.  
  
## Syntaxe  
  
```  
dateTimeFormatObj.format  
```  
  
#### Paramètres  
 `dateTimeFormatObj`  
 Requis.  Nom de l'objet `DateTimeFormat` à utiliser comme formateur.  
  
## Notes  
 La fonction retournée par la propriété `format` accepte un seul argument, `date`, et retourne une chaîne qui représente la date localisée en utilisant les options spécifiées dans l'objet `DateTimeFormat`.  Le paramètre `date` de la fonction retournée doit être un nombre, une chaîne de date ou un objet `Date`.  Si `date` n'est pas fourni, la fonction utilise [Date.now](../../javascript/reference/date-now-function-javascript.md) comme valeur d'entrée par défaut.  
  
## Exemple  
 L'exemple suivant utilise un objet `DateTimeFormat` pour localiser la date « 1er décembre 2007 » en allemand et la remettre en forme.  
  
```javascript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [Intl.DateTimeFormat, objet](../../javascript/reference/intl-datetimeformat-object-javascript.md)