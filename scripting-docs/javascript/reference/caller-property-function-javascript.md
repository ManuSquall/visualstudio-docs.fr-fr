---
title: "caller, propri&#233;t&#233; (Function) (JavaScript) | Microsoft Docs"
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
  - "caller"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "caller (propriété)"
  - "appels de fonction, fonctions exécutées"
ms.assetid: ae210853-7160-4102-9cfd-ab489f180ce1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# caller, propri&#233;t&#233; (Function) (JavaScript)
Obtient la fonction qui a appelé la fonction active.  
  
## Syntaxe  
  
```  
  
functionName.caller  
```  
  
## Notes  
 L'objet `functionName` est le nom de toute fonction en cours d'exécution.  
  
 La propriété `caller` est définie uniquement pour une fonction en cours d'exécution.  \+Si la fonction est appelée à partir du niveau supérieur d'un programme [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], la propriété `caller` a la valeur `null`.  
  
 Si la propriété `caller` est utilisée dans un contexte de chaîne, le résultat est le même qu'avec `functionName``toString`, c'est\-à\-dire que c'est le texte décompilé de la fonction qui est affiché.  
  
 L'exemple suivant illustre l'utilisation de la propriété `caller` :  
  
```javascript  
function CallLevel(){  
   if (CallLevel.caller == null)  
      return("CallLevel was called from the top level.");  
   else  
      return("CallLevel was called by another function.");  
}  
  
document.write(CallLevel());  
  
// Output: CallLevel was called from the top level.  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [function, instruction](../../javascript/reference/function-statement-javascript.md)