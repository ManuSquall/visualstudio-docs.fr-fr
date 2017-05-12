---
title: "toString, m&#233;thode (Boolean) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString, m&#233;thode (Boolean)
Retourne la représentation d'un objet sous forme de chaîne.  
  
## Syntaxe  
  
```  
  
boolean.toString()  
```  
  
## Paramètres  
 `boolean`  
 Obligatoire.  Objet pour lequel une représentation sous forme de chaîne doit être obtenue.  
  
## Valeur de retour  
 Si la valeur booléenne est `true`, elle retourne la valeur « true ».  Sinon, elle retourne la valeur « false ».  
  
## Notes  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode **toString**.  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]