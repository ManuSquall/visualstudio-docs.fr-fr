---
title: "callee, propri&#233;t&#233; (arguments) (JavaScript) | Microsoft Docs"
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
  - "callee"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "callee (propriété)"
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# callee, propri&#233;t&#233; (arguments) (JavaScript)
Retourne l'objet de la `Function` en cours d'exécution, en l'occurrence le corps du texte de l'objet `Function` spécifié.  
  
## Syntaxe  
  
```  
[function.]arguments.callee  
```  
  
## Notes  
 L'argument *function* facultatif est le nom de l'objet `Function` en cours d'exécution.  
  
 La propriété `callee` est un membre de l'objet **d' arguments** qui ne devient disponible que lorsque la fonction associée est en cours d'exécution.  
  
 La valeur initiale de la propriété `callee` correspond à l'objet `Function` en cours d'exécution.  Cela permet aux fonctions anonymes d'être récursives.  
  
## Exemple  
  
```javascript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [arguments, objet](../../javascript/reference/arguments-object-javascript.md)&#124; [Objet de function](../../javascript/reference/function-object-javascript.md)  
  
## Voir aussi  
 [caller, propriété \(Function\)](../../javascript/reference/caller-property-function-javascript.md)