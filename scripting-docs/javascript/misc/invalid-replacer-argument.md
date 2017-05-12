---
title: "Argument de remplacement non valide | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Argument de remplacement non valide
Tentative d'appel de `JSON.stringify` avec un argument non valide.  L'argument `replacer` doit être une fonction ou un tableau.  
  
### Pour corriger cette erreur  
  
-   Transformez l'argument `replacer` en fonction ou en tableau.  
  
## Exemple  
 Le code de cet exemple génère une erreur d'exécution car `memberfilter` est un objet au lieu d'une fonction ou d'un tableau.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## Voir aussi  
 [JSON, objet](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse, fonction](../../javascript/reference/json-parse-function-javascript.md)   
 [Erreurs d'exécution JavaScript](../../javascript/reference/javascript-run-time-errors.md)