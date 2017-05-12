---
title: "leftContext, propri&#233;t&#233; ($&#39;) (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$`"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "leftContext (propriété) ($`)"
ms.assetid: 840e56c0-eb7c-461f-bb56-91acff9b5bcf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# leftContext, propri&#233;t&#233; ($&#39;) (RegExp) (JavaScript)
Retourne les caractères à partir du début de la chaîne recherchée jusqu'à la position avant le début la dernière correspondance.  Lecture seule.  
  
## Syntaxe  
  
```  
  
RegExp.leftContext  
```  
  
## Notes  
 L'objet associé à cette propriété est toujours l'objet `RegExp` global.  
  
 La valeur initiale de la propriété `leftContext` est une chaîne vide.  La valeur de la propriété `leftContext` change chaque fois qu'une correspondance est trouvée.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la propriété `leftContext` :  
  
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
 [lastParen, propriété \($\+\) \(RegExp\)](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [rightContext, propriété \($'\) \(RegExp\)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)