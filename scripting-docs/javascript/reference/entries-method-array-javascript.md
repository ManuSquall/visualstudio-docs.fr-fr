---
title: "entries, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9bc46afb-74d2-4f99-8c95-f46475acf21d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# entries, m&#233;thode (Array) (JavaScript)
Retourne un itérateur qui retourne les paires clé\/valeur du tableau.  
  
## Syntaxe  
  
```  
arrayObj.entries();  
```  
  
#### Paramètres  
 `arrayObj`  
 Obligatoire.  Objet Array.  
  
## Notes  
  
## Exemple  
 L'exemple suivant montre comment obtenir les paires clé\/valeur d'un tableau.  
  
```javascript  
var entries = ["a", "b", "c"].entries();  
// entries.next().value == [0, "a"]  
// entries.next().value == [1, "b"]  
// entries.next().value == [2, "c"]   
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]