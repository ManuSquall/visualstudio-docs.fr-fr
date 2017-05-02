---
title: "toGMTString, m&#233;thode (Date) (JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString (méthode)"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toGMTString, m&#233;thode (Date) (JavaScript)
Retourne une date convertie en chaîne selon le format GMT \(Greenwich Mean Time\).  
  
## Syntaxe  
  
```  
  
dateObj.toGMTString()   
```  
  
## Notes  
 La référence `dateObj` requise est un objet `Date`.  
  
 La méthode `toGMTString` est obsolète et n'est plus utilisée qu'à des fins de compatibilité descendante.  Il est recommandé d'utiliser plutôt la méthode `toUTCString`.  
  
 La méthode `toGMTString` retourne un objet `String` contenant la date mise en forme selon la convention GMT.  Le format de la valeur de retour est le suivant : « 05 Jan 1996 00:00:00 GMT. »  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Date, objet](../../javascript/reference/date-object-javascript.md)  
  
## Voir aussi  
 [toUTCString, méthode \(Date\)](../../javascript/reference/toutcstring-method-date-javascript.md)