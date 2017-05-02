---
title: "includes, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# includes, m&#233;thode (String) (JavaScript)
Retourne une valeur booléenne qui indique si la chaîne passée est contenue dans l'objet String.  
  
## Syntaxe  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### Paramètres  
 `stringObj`  
 Obligatoire.  Objet String pour le test.  
  
 `substring`  
 Obligatoire.  Chaîne à tester.  
  
 `position`  
 Facultatif.  Position du premier caractère pour le test dans l'objet String, en commençant à 0.  
  
## Valeur de retour  
 Si la chaîne passée est contenue dans l'objet String, la méthode `includes` retourne `true` ; sinon, elle retourne `false`.  
  
## Notes  
  
## Exemple  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]