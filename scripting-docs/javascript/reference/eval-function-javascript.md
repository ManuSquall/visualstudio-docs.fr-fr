---
title: "eval, fonction (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval (fonction)"
  - "analyse, code"
  - "analyseur"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# eval, fonction (JavaScript)
Évalue le code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et l'exécute.  
  
## Syntaxe  
  
```  
eval(codeString)   
```  
  
## Paramètres  
 `codeString`  
 Obligatoire.  Valeur de `String` qui contient du code [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valide.  
  
## Notes  
 La fonction `eval` autorise l'exécution dynamique de code source [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 La chaîne `codeString` est analysée par l'analyseur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] et exécutée.  
  
 Le code passé à la fonction `eval` est exécuté dans le même contexte que l'appel à la fonction `eval`.  
  
 Dans la mesure du possible, utilisez la [fonction JSON.parse](../../javascript/reference/json-parse-function-javascript.md) pour désérialiser le texte JSON \(JavaScript Object Notation\).  La fonction `JSON.parse` est plus sûre et exécute plus rapidement que la fonction `eval`.  
  
## Exemple  
 Le code suivant initialise la variable `myDate` à une date de test.  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Voir aussi  
 [String, objet](../../javascript/reference/string-object-javascript.md)