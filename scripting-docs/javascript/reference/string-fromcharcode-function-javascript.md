---
title: "String.fromCharCode, fonction (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCode (méthode)"
  - "caractères, à partir d’Unicode"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# String.fromCharCode, fonction (JavaScript)
Retourne une chaîne à partir d'un certain nombre de valeurs de caractères Unicode.  
  
## Syntaxe  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## Paramètres  
 `String`  
 Obligatoire.  Objet `String`.  
  
 `code1`, . . . , `codeN`  
 Facultatif.  Série de valeurs de caractères Unicode à convertir en chaîne.  Si aucun argument n'est spécifié, le résultat est une chaîne vide.  
  
## Notes  
 Vous appelez cette fonction sur l'objet `String` plutôt que sur une instance de chaîne.  
  
 L'exemple suivant illustre l'utilisation de cette méthode :  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [charCodeAt, méthode \(String\)](../../javascript/reference/charcodeat-method-string-javascript.md)