---
title: "exec, m&#233;thode (Regular Expression) (JavaScript) | Microsoft Docs"
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
  - "exec"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Exec (méthode)"
  - "mise en correspondance de chaînes"
ms.assetid: 83092452-60cc-4218-b4ae-af9e3cb96c34
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# exec, m&#233;thode (Regular Expression) (JavaScript)
Exécute une recherche sur une chaîne à l'aide d'un modèle d'expression régulière et retourne les résultats de cette recherche, sous forme de tableau.  
  
## Syntaxe  
  
```  
  
rgExp.exec(str)   
```  
  
## Paramètres  
 `rgExp`  
 Obligatoire.  Instance d'un objet **Regular Expression** contenant le modèle d'expression régulière et les indicateurs applicables.  
  
 `str`  
 Obligatoire.  Objet `String` ou littéral de chaîne sur lequel effectuer la recherche.  
  
## Notes  
 Si la méthode `exec` ne trouve aucune correspondance, elle retourne la valeur `null`.  Dans le cas contraire, `exec` retourne un tableau et les propriétés de l'objet `RegExp` global sont mises à jour pour refléter les résultats de la correspondance.  L'élément zéro du tableau contient la correspondante complète, alors que les éléments 1 à *n* contiennent les sous\-chaînes trouvées à l'intérieur de la correspondance.  Ce comportement est identique à celui de la méthode `match` sans définition de l'indicateur global \(**g**\).  
  
 Si ce dernier est défini pour une expression régulière, la méthode `exec` recherche la chaîne à partir de la position indiquée par la valeur de la propriété `lastIndex`.  Si l'indicateur global n'est pas défini, `exec` ignore la valeur de la propriété `lastIndex` et effectue la recherche à partir du début de la chaîne.  
  
 Le tableau retourné par la méthode `exec` possède trois propriétés, à savoir **input**, **index** et **lastIndex**. La propriété **input** contient la chaîne recherchée dans son intégralité.  La propriété **index** contient la position de la sous\-chaîne trouvée à l'intérieur de la chaîne recherchée complète.  La propriété `lastIndex` contient la position suivant le dernier caractère de la correspondance.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `exec` :  
  
```javascript  
function RegExpTest()  
{  
   var ver = Number(ScriptEngineMajorVersion() + "." + ScriptEngineMinorVersion())  
   if (ver < 5.5)  
   {  
      document.write("You need a newer version of JavaScript for this to work");  
      return;  
   }  
  
   var src = "The quick brown fox jumps over the lazy dog.";  
  
   // Create regular expression pattern with a global flag.  
   var re = /\w+/g;  
  
   // Get the next word, starting at the position of lastindex.  
   var arr;  
   while ((arr = re.exec(src)) != null)  
      {  
      // New line:  
      document.write ("<br />");    
      document.write (arr.index + "-" + arr.lastIndex + " ");  
      document.write (arr[0]);  
      }  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)  
  
## Voir aussi  
 [match, méthode \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [search, méthode \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test, méthode \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/fr-fr/3b62e27c-4f07-4726-a95b-6e841807bfaf)