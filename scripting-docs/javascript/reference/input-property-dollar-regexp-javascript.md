---
title: "input, propri&#233;t&#233; ($_) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$_"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "$_ (propriété)"
  - "input (propriété)"
ms.assetid: 88c6d1d8-56f7-4334-a7eb-e899aec9cda4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# input, propri&#233;t&#233; ($_) (RegExp) (JavaScript)
Retourne la chaîne sur laquelle une recherche d'expression régulière a été effectuée.  Lecture seule.  
  
## Syntaxe  
  
```  
  
RegExp.input  
```  
  
## Notes  
 L'objet associé à cette propriété est toujours l'objet `RegExp` global.  
  
 La valeur de la propriété **input** est modifiée chaque fois que la chaîne recherchée est modifiée.  
  
 L'exemple ci\-dessous illustre l'utilisation de la propriété **input** :  
  
```javascript  
function inputDemo(){  
   var s;  
   var re = new RegExp("d(b+)(d)","ig");  
   var str = "cdbBdbsbdbdz";  
   var arr = re.exec(str);  
   s = "The string used for the match was " + RegExp.input;   
   return(s);  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)  
  
## Voir aussi  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)