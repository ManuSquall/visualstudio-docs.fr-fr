---
title: "lastParen, propri&#233;t&#233; ($+) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastParen (propriété) ($+)"
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# lastParen, propri&#233;t&#233; ($+) (RegExp) (JavaScript)
Retourne la dernière sous\-correspondance entre parenthèses d'une recherche d'expression régulière, le cas échéant.  Lecture seule.  
  
## Syntaxe  
  
```  
  
RegExp.lastParen  
```  
  
## Notes  
 L'objet associé à cette propriété est toujours l'objet `RegExp` global.  
  
 La valeur initiale de la propriété `lastParen` est une chaîne vide.  Sa valeur change chaque fois qu'une correspondance est trouvée.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété `lastParen` :  
  
```javascript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)  
  
## Voir aussi  
 [$1...$9, propriétés \(RegExp\)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [index, propriété \(RegExp\)](../../javascript/reference/index-property-regexp-javascript.md)   
 [input, propriété \($\_\) \(RegExp\)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex, propriété \(RegExp\)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [lastMatch, propriété \($%\) \(RegExp\)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [leftContext, propriété \($'\) \(RegExp\)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext, propriété \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)