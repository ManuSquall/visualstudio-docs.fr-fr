---
title: "valueOf, m&#233;thode (Error) | Microsoft Docs"
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
ms.assetid: ca25c57d-c9ad-445b-8235-561390de680c
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf, m&#233;thode (Error)
Retourne la valeur de chaîne d'une erreur.  
  
## Syntaxe  
  
```  
  
error.valueOf()  
```  
  
#### Paramètres  
 L'objet `error` est une instance d'une erreur.  
  
## Valeur de retour  
 Chaîne « Erreur : » ainsi que le message d'erreur.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode `valueOF` avec une date.  
  
```javascript  
var myError = new Error();  
myError.message = "This is an error.";  
var value = myError.valueOf();  
document.write(value);  
  
// Output: Error: This is an error.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]