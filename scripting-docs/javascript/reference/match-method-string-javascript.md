---
title: "match, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "match"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Match (méthode)"
ms.assetid: eda9ad27-4f9b-4cb1-8345-a0ae85979ca0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# match, m&#233;thode (String) (JavaScript)
Correspond à une chaîne avec une expression régulière et retourne un tableau contenant les résultats de cette recherche.  
  
## Syntaxe  
  
```  
  
stringObj.match(rgExp)   
```  
  
## Paramètres  
 `stringObj`  
 Requis.  Objet `String` ou littéral de chaîne sur lequel s'effectue la recherche.  
  
 `rgExp`  
 Requis.  Objet d'expression régulière contenant le modèle d'expression régulière et les indicateurs applicables.  Ce peut être également le nom d'une variable ou un littéral de chaîne contenant le modèle d'expression régulière et les indicateurs.  
  
## Notes  
 Si la méthode `match` ne trouve aucune correspondance, elle retourne la valeur `null`.  Dans le cas contraire, `match` retourne un tableau, et les propriétés de l'objet `RegExp` global sont mises à jour pour refléter les résultats de la recherche.  
  
 Si l'indicateur global \(`g`\) n'est pas défini, l'élément zéro du tableau contient la chaîne correspondante intégrale ; les éléments 1 à *n* contiennent les sous\-chaînes trouvées à l'intérieur de la correspondance.  Ce comportement est identique à celui de la [exec, méthode \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md) lorsque l'indicateur global n'est pas défini.  Si ce dernier est défini, les éléments 0 \- *n* contiennent toutes les correspondances qui ont été trouvées.  
  
 Si l'indicateur global n'est pas défini, le tableau retourné par la méthode `match` a deux propriétés, `input` et `index`.  La propriété `input` contient la chaîne recherchée dans son intégralité.  La propriété `index` contient la position de la sous\-chaîne trouvée à l'intérieur de la chaîne recherchée complète.  
  
 Si l'indicateur `i` est défini, la recherche ne respecte pas la casse.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `match`.  
  
```javascript  
var src = "azcafAJAC";  
  
var re = /[a-c]/;  
  
var result = src.match(re);  
  
// The entire match is in array element 0.  
document.write(result[0] + "<br/>");  
  
// Now try the same match with the global flag.  
var reg = /[a-c]/g;  
result = src.match(reg);  
  
// The matches are in elements 0 through n.  
for (var index = 0; index < result.length; index++)  
{  
    document.write ("submatch " + index + ": " +  result[index]);  
    document.write("<br />");  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [exec, méthode \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)   
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [replace, méthode \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [search, méthode \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test, méthode \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/fr-fr/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternation and Subexpressions \(JavaScript\)](http://msdn.microsoft.com/fr-fr/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Backreferences \(JavaScript\)](http://msdn.microsoft.com/fr-fr/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)