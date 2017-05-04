---
title: "RegExp, objet (JavaScript) | Microsoft Docs"
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
  - "RegExp"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp (objet)"
  - "RegExp (objet), vue d'ensemble"
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# RegExp, objet (JavaScript)
Objet global intrinsèque stockant des informations sur les résultats des correspondances avec le modèle d'expression régulière.  
  
## Syntaxe  
  
```  
  
RegExp.property   
```  
  
## Notes  
 L'argument de *propriété* requis peut être l'une des propriétés de l'objet `RegExp`.  
  
 L'objet `RegExp` ne peut pas être créé directement, mais il est toujours disponible.  Les valeurs initiales des différentes propriétés de l'objet `RegExp` sont les suivantes jusqu'à ce qu'une recherche d'expression régulière ait été réalisée avec succès :  
  
|Propriété|Raccourci|Valeur initiale|  
|---------------|---------------|---------------------|  
|index||\-1|  
|input|$\_|Chaîne vide.|  
|lastIndex||\-1|  
|lastMatch|$&|Chaîne vide.|  
|lastParen|$\+|Chaîne vide.|  
|leftContext|$\`|Chaîne vide.|  
|rightContext|$'|Chaîne vide.|  
|$1 \- $9|$1 \- $9|Chaîne vide.|  
  
 Ses propriétés ont des valeurs indéfinies jusqu'à ce qu'une recherche réussie d'expression régulière ait été effectuée.  
  
 L'objet `RegExp` global ne doit pas être confondu avec l'objet **Regular Expression**.  Bien qu'ils semblent identiques, ils sont distincts et séparés.  Les propriétés de l'objet `RegExp` contiennent des informations mises à jour en permanence sur chacune des correspondances trouvées. En revanche, les propriétés de l'objet **Regular Expression** ne contiennent que les informations relatives aux correspondances ayant été trouvées avec cette instance particulière de l'**expression régulière**.  
  
## Exemple  
 L'exemple suivant effectue une recherche d'expression régulière.  Il affiche les correspondances et sous\-correspondances à partir de l'objet `RegExp` global et du tableau qui est retourné par la méthode `exec`.  
  
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
  
<a name="js56jsobjregexpprop"></a>   
## Propriétés  
 [$1…$9, propriétés](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index, propriété](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input, propriété](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex, propriété](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [lastMatch, propriété](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [lastParen, propriété](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext, propriété](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [rightContext, propriété](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## Méthodes  
 L'objet `RegExp` n'a pas de méthodes.  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String, objet](../../javascript/reference/string-object-javascript.md)