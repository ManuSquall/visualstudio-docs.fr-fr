---
title: "R&#233;f&#233;rence circulaire dans l&#39;argument de valeur non prise en charge | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5034"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# R&#233;f&#233;rence circulaire dans l&#39;argument de valeur non prise en charge
Tentative d'appel de `JSON.stringify` avec une valeur qui n'est pas valide.  L'argument `value`, un tableau ou un objet, contient une référence circulaire.  
  
### Pour corriger cette erreur  
  
-   Supprimez la référence circulaire de l'argument.  
  
## Exemple  
 Le code de l'exemple suivant provoque une erreur d'exécution car `john` comporte une référence à `mary` et `mary` comporte une référence à `john`.  pour supprimer la référence circulaire, supprimez ou annulez la propriété `brother` de l'objet `mary` ou la propriété `sister` de l'objet `john`.  
  
```javascript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## Voir aussi  
 [JSON, objet](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse, fonction](../../javascript/reference/json-parse-function-javascript.md)   
 [Erreurs d'exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)