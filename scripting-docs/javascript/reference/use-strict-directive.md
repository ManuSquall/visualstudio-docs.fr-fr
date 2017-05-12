---
title: "use strict, directive | Microsoft Docs"
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
  - "strict_JavaScriptKeyword"
  - "use strict"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "mode strict"
  - "use strict (directive)"
  - "use strict"
ms.assetid: b532e8c9-548c-4bbe-b2fc-5459ebd62e56
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# use strict, directive
Limite l'utilisation de certaines fonctionnalités dans JavaScript.  Pris en charge dans Internet Explorer 10 et dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] uniquement.  
  
## Syntaxe  
  
```javascript  
use strict  
```  
  
## Notes  
  
## Exemple  
 Le code suivant provoque une erreur de syntaxe. En effet, en mode strict, toutes les variables doivent être déclarées avec le préfixe `var`.  
  
```javascript  
"use strict";  
function testFunction(){  
   var testvar = 4;  
    return testvar;  
}  
intvar = 5;  
  
```  
  
## Voir aussi  
 [Mode strict](../../javascript/advanced/strict-mode-javascript.md)