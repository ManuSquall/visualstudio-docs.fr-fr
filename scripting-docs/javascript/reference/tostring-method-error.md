---
title: "toString, m&#233;thode (Error) | Microsoft Docs"
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
ms.assetid: 5d6d9712-c06d-4b31-9bc9-e46f6bb5cd38
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString, m&#233;thode (Error)
Retourne la représentation d'une erreur sous forme de chaîne.  
  
## Syntaxe  
  
```  
  
error.toString()  
```  
  
## Paramètres  
 `date`  
 Obligatoire.  Erreur à représenter en tant que chaîne.  
  
## Valeur de retour  
 Retourne « Erreur : », ainsi que le message d'erreur.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la méthode `toString` avec une erreur.  
  
```javascript  
var myError = new Error();  
myError.message = "My Error";  
var errorString = myError.toString();  
document.write(errorString);  
  
// Output: Error: My Error  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]