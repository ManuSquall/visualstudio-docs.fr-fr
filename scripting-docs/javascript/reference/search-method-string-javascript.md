---
title: "search, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search (méthode)"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# search, m&#233;thode (String) (JavaScript)
Recherche la première correspondance de sous\-chaîne dans une recherche d'expression régulière.  
  
## Syntaxe  
  
```  
  
stringObj.search(rgExp)   
```  
  
## Paramètres  
 `stringObj`  
 Obligatoire.  Objet `String` ou littéral de chaîne sur lequel effectuer la recherche.  
  
 `rgExp`  
 Obligatoire.  Instance d'un objet **Regular Expression** contenant le modèle d'expression régulière et les indicateurs applicables.  
  
## Valeur de retour  
 Si une correspondance est trouvée, la méthode **search** retourne une valeur entière qui indique l'offset à partir du début de la chaîne où la première correspondance a été identifiée.  En l'absence de correspondance, elle retourne la valeur \-1.  
  
## Notes  
 Vous pouvez également définir l'indicateur `i` qui rend la recherche non sensible à la casse.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **search**.  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [exec, méthode \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match, méthode \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace, méthode \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [test, méthode \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/fr-fr/3b62e27c-4f07-4726-a95b-6e841807bfaf)