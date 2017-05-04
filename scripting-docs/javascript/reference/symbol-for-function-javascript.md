---
title: "Symbol.for, fonction (JavaScript) | Microsoft Docs"
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
ms.assetid: 27db15f3-9108-4892-8f89-e84031729cb6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Symbol.for, fonction (JavaScript)
Retourne le symbole d'une clé spécifiée ou, si la clé n'est pas présente, crée un objet symbole avec la nouvelle clé.  
  
## Syntaxe  
  
```vb  
Symbol.for(key);  
```  
  
#### Paramètres  
 `key`  
 Obligatoire.  Clé du symbole, également utilisée comme description.  
  
## Notes  
 Cette méthode recherche le symbole dans le Registre des symboles globaux.  Si vous sérialisez les symboles en tant que chaînes, utilisez le Registre des symboles globaux pour être certain qu'une chaîne particulière correspond au symbole approprié pour toutes les recherches.  
  
## Exemple  
  
```javascript  
var sym = Symbol.for("desc");  
  
console.log(sym.toString());  
  
// Two different object references.  
console.log(Symbol("symbol") === Symbol.for("symbol");)  
// Single object reference.   
console.log(Symbol.for("symbol") === Symbol.for("symbol");)  
  
// Output:  
// Symbol(desc);  
// false  
// true  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]