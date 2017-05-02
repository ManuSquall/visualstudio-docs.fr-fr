---
title: "getVarDate, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "getVarDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objet)"
  - "getVarDate (méthode)"
  - "dates, format VT_DATE"
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# getVarDate, m&#233;thode (Date) (JavaScript)
Retourne une valeur VT\_DATE d’un objet `Date`.  
  
> [!WARNING]
>  Cette méthode est prise en charge seulement dans Internet Explorer.  
  
## Syntaxe  
  
```  
  
dateObj.getVarDate()   
```  
  
#### Paramètres  
 La référence `dateObj` nécessaire est un objet `Date`.  
  
## Valeur de retour  
 Retourne une valeur VT\_DATE.  
  
## Notes  
 La méthode `getVarDate` est utilisée quand du code JavaScript interagit avec des objets COM, des objets ActiveX ou d’autres objets qui acceptent et retournent des valeurs de date au format VT\_DATE. Il s’agit notamment d’objets dans Visual Basic et Visual Basic Scripting Edition \(VBScript\). Le format réel de la valeur retournée dépend des paramètres régionaux.  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\) et Internet Explorer 10 \(mode standard\). Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Voir [Informations de version](../../javascript/reference/javascript-version-information.md).  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [getDate, méthode \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse, fonction](../../javascript/reference/date-parse-function-javascript.md)