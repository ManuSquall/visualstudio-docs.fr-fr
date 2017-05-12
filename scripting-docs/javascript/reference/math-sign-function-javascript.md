---
title: "Math.sign, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Math.sign, fonction (JavaScript)
Retourne le signe d'un nombre indiquant si celui\-ci est positif, négatif ou égal à 0.  
  
## Syntaxe  
  
```  
Math.sign(number)  
```  
  
## Notes  
 L'argument `number` requis est une expression numérique pour laquelle le signe est nécessaire.  
  
 La valeur de retour est l'une des suivantes :  
  
-   `NaN`, si `number` est `NaN`.  
  
-   \-0, si `number` est −0.  
  
-   \+0, si `number` est \+0.  
  
-   \-1, si `number` est négatif et différent de −0.  
  
-   \+1, si `number` est positif et différent de \+0.  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]