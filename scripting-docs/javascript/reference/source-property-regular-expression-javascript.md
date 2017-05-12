---
title: "source, propri&#233;t&#233; (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "source"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Source (propriété)"
ms.assetid: d58ac57e-fcde-49d1-bbba-e8c4218448c4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# source, propri&#233;t&#233; (Regular Expression) (JavaScript)
Retourne une copie du texte du modèle d'expression régulière.  Lecture seule.  L'argument `rgExp` est un objet d'**Regular expression**.  Ce peut être un nom de variable ou un littéral.  
  
## Syntaxe  
  
```  
  
rgExp.source  
```  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la propriété **source** :  
  
```javascript  
function SourceDemo(re, s){  
   var s1;  
   // Test string for existence of regular expression.  
   if (re.test(s))  
      s1 = " contains ";  
   else  
      s1 = " does not contain ";  
   // Get the text of the regular expression itself.  
   return(s + s1 + re.source);  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)