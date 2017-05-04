---
title: "format, propri&#233;t&#233; (Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# format, propri&#233;t&#233; (Intl.NumberFormat)
Retourne une fonction qui met un nombre en forme spécifique aux paramètres régionaux à l'aide des paramètres du formateur de nombres spécifiés.  
  
## Syntaxe  
  
```  
numberFormatObj.format  
```  
  
#### Paramètres  
 `numberFormatObj`  
 Requis.  Nom de l'objet `NumberFormat` à utiliser comme formateur.  
  
## Notes  
 La fonction retournée par la propriété `format` accepte un seul argument, `value`, et retourne une chaîne qui représente le nombre localisé en utilisant les options spécifiées dans l'objet `NumberFormat`.  Si `value` n'est pas fourni, la fonction retourne `NaN` \(pas un nombre\).  
  
## Exemple  
 L'exemple suivant utilise un objet `NumberFormat` pour créer un nombre localisé.  
  
```javascript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [Intl.NumberFormat, objet](../../javascript/reference/intl-numberformat-object-javascript.md)