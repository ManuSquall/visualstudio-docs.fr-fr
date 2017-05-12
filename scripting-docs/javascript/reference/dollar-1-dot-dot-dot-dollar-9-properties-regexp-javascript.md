---
title: "$1...$9, propri&#233;t&#233;s (RegExp) (JavaScript) | Microsoft Docs"
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
  - "$1...$9"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propriétés $1...$9"
ms.assetid: 8bd84851-f62f-4eb1-a93d-b67135ea091a
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# $1...$9, propri&#233;t&#233;s (RegExp) (JavaScript)
Retournent les neuf dernières sous\-chaînes stockées parmi celles qui ont été trouvées lors de la recherche de correspondances d'un modèle dans une expression régulière.  Lecture seule.  
  
## Syntaxe  
  
```  
  
RegExp.$n   
```  
  
## Paramètres  
 `RegExp`  
 Toujours l'objet `RegExp` global.  
  
 `n`  
 Tout entier compris entre 1 et 9.  
  
## Notes  
 Les valeurs des propriétés **$1…$9** changent chaque fois qu'une correspondance entre parenthèses est trouvée.  Un nombre quelconque de sous\-chaînes entre parenthèses peut être spécifié dans un modèle d'expression régulière, mais seules les neuf plus récentes peuvent être stockées.  
  
## Exemple  
 L'exemple suivant effectue une recherche d'expression régulière.  Il affiche les correspondances et des sous\-correspondances de l'objet `RegExp` global.  Les sous\-correspondances sont des correspondances entre parenthèses réussies qui sont contenues dans les propriétés `$1…$9`.  L'exemple affiche également des correspondances et des sous\-correspondances du tableau retourné par la méthode `exec`.  
  
```javascript  
var newLine = "<br />";  
  
var re = /(\w+)@(\w+)\.(\w+)/g  
var src = "Please send mail to george@contoso.com and someone@example.com. Thanks!"  
  
var result;  
var s = "";  
  
// Get the first match.  
result = re.exec(src);  
  
while (result != null) {  
    // Show the entire match.  
    s += newLine;  
  
    // Show the match and submatches from the RegExp global object.  
    s += "RegExp.lastMatch: " + RegExp.lastMatch + newLine;  
    s += "RegExp.$1: " + RegExp.$1 + newLine;  
    s += "RegExp.$2: " + RegExp.$2 + newLine;  
    s += "RegExp.$3: " + RegExp.$3 + newLine;  
  
    // Show the match and submatches from the array that is returned  
    // by the exec method.  
    for (var index = 0; index < result.length; index++) {  
        s +=  index + ": ";  
        s += result[index];  
        s += newLine;  
    }  
  
    // Get the next match.  
    result = re.exec(src);  
}  
document.write(s);  
  
// Output:  
//  RegExp.lastMatch: george@contoso.com  
//  RegExp.$1: george  
//  RegExp.$2: contoso  
//  RegExp.$3: com  
//  0: george@contoso.com  
//  1: george  
//  2: contoso  
//  3: com  
  
//  RegExp.lastMatch: someone@example.com  
//  RegExp.$1: someone  
//  RegExp.$2: example  
//  RegExp.$3: com  
//  0: someone@example.com  
//  1: someone  
//  2: example  
//  3: com  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)  
  
## Voir aussi  
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)