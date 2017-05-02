---
title: "&#39;Throw&#39; doit &#234;tre suivi d&#39;une expression sur la m&#234;me ligne source | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# &#39;Throw&#39; doit &#234;tre suivi d&#39;une expression sur la m&#234;me ligne source
Le mot clé `throw` n'a pas été suivi par une expression dans la même ligne source.  Une instruction `throw` se compose de deux parties : le mot clé `throw`, suivi de l'expression à lever.  Par exemple :  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Vous ne pouvez pas dissocier ces deux composants.  
  
### Pour corriger cette erreur  
  
-   Assurez \-vous que le mot clé `throw` et l'expression à lever figurent sur la même ligne.  
  
## Voir aussi  
 [Error, objet](../../javascript/reference/error-object-javascript.md)   
 [Instruction throw](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)