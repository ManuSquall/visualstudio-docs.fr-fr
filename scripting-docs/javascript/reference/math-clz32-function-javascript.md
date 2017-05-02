---
title: "Fonction Math.clz32 (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Fonction Math.clz32 (JavaScript)
Retourne le nombre de zéros d'en\-tête de la représentation binaire 32 bits d'un nombre.  
  
## Syntaxe  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## Notes  
 Si `number` vaut 0, le résultat est 32.  Si le bit le plus significatif de l'encodage binaire 32 bits de `number` est 1, le résultat est égal à 0.  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)