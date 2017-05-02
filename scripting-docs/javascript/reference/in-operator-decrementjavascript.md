---
title: "in, op&#233;rateur (JavaScript) | Microsoft Docs"
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
  - "in_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "in (opérateur)"
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# in, op&#233;rateur (JavaScript)
Vérifie l'existence d'une propriété dans un objet.  
  
## Syntaxe  
  
```  
  
result = property in object  
```  
  
## Paramètres  
 `result`  
 Obligatoire.  Toute variable.  
  
 `property`  
 Obligatoire.  Expression retournant une expression de chaîne.  
  
 `object`  
 Obligatoire.  N'importe quel objet.  
  
## Notes  
 L'opérateur `in` détermine si un objet possède une propriété nommée `property`.  Il détermine également si la propriété fait partie de la chaîne des prototypes de l'objet.  Pour plus d'informations sur les prototypes d'objet, consultez [Prototypes et héritage de prototypes](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'opérateur `in` :  
  
```javascript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)