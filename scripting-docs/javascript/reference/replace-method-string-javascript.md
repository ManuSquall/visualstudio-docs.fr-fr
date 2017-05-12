---
title: "replace, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "replace"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Replace (méthode)"
  - "remplacer des chaînes"
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# replace, m&#233;thode (String) (JavaScript)
Remplace du texte dans une chaîne, à l'aide d'une expression régulière ou d'une chaîne de recherche.  
  
## Syntaxe  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## Paramètres  
 `stringObj`  
 Obligatoire.  Objet `String` ou littéral de chaîne sur lequel effectuer le remplacement.  Cette chaîne n'est pas modifiée par la méthode **replace**.  Au lieu de cela, la valeur de retour de cette méthode est la chaîne produite par le remplacement.  
  
 `rgExp`  
 Obligatoire.  Instance d'un objet **Regular Expression**  contenant le modèle d'expression régulière et les indicateurs applicables.  Peut également être un objet `String` ou un littéral de chaîne qui représente l'expression régulière.  Si l'argument `rgExp` n'est pas une instance d'un objet **Regular Expression**, il est converti en chaîne, et une recherche exacte est lancée ; aucune tentative n'est faite pour convertir la chaîne en expression régulière.  
  
 `replaceText`  
 Obligatoire.  Objet `String` ou littéral de chaîne contenant le texte de remplacement pour chaque correspondance trouvée de `rgExp` dans `stringObj`.  Dans [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure, l'argument `replaceText` peut également être une fonction qui retourne le texte de remplacement.  
  
## Valeur de retour  
 Le résultat de la méthode **replace** est une copie de `stringObj` une fois que les remplacements spécifiés ont été effectués.  
  
## Notes  
 Les variables de correspondance suivantes peuvent toutes être utilisées pour identifier la correspondance la plus récente ainsi que la chaîne où elle se situe.  Ces variables peuvent être employées dans le texte de remplacement où la chaîne de remplacement doit être déterminée de façon dynamique.  
  
|Caractères|Signification|  
|----------------|-------------------|  
|**$$**|`$` \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure\)|  
|**$&**|Spécifie la partie de `stringObj` que l'ensemble du modèle a trouvée.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure\)|  
|`$``|Spécifie la partie de `stringObj` qui précède la correspondance décrite par **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure\)|  
|`$'`|Spécifie la partie de `stringObj` qui suit la correspondance décrite par **$&**.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure\)|  
|`$`  ***n***|*n*ième sous\-correspondance capturée, où *n* est un chiffre décimal unique de 1 à 9.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure\)|  
|`$`  ***nn***|*nn*ième sous\-correspondance capturée, où *nn* est un nombre décimal à deux chiffres de 01 à 99.  \([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure\)|  
  
 Si `replaceText` est une fonction, celle\-ci est appelée pour chaque sous\-chaîne trouvée avec les arguments *m* \+ 3 suivants, où *m* représente le nombre de parenthèses de capture situées à gauche dans `rgExp`.  Le premier argument correspond à la sous\-chaîne trouvée.  Les *m* arguments suivants sont les captures résultant de la recherche.  L'argument *m* \+ 2 correspond au décalage dans `stringObj` où la correspondance a été trouvée, et l'argument *m* \+ 3 est `stringObj`.  Le résultat est la valeur de chaîne obtenue après le remplacement de chaque sous\-chaîne trouvée par la valeur de retour correspondante de l'appel de fonction.  
  
 La méthode **replace** met à jour les propriétés de l'objet `RegExp` global.  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode **replace** pour remplacer toutes les instances du mot « the » par « a ».  
  
```javascript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 En outre, la méthode **replace** peut également remplacer des sous\-expressions dans le modèle.  L'exemple suivant permute chaque paire de mots dans la chaîne.  
  
```javascript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 L'exemple suivant, qui fonctionne dans [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] et les versions ultérieures, montre comment utiliser une fonction qui retourne le texte de remplacement.  Il remplace toute instance d'un nombre suivi de « F » par une conversion en degrés Celsius.  
  
```javascript  
function f2c(s1) {  
    // Initialize pattern.  
    var test = /(\d+(\.\d*)?)F\b/g;  
  
    // Use a function for the replacement.  
    var s2 = s1.replace(test,  
      function($0,$1,$2)  
           {   
           return((($1-32) * 5/9) + "C");  
           }  
        )  
    return s2;  
}  
document.write(f2c("Water freezes at 32F and boils at 212F."));  
  
// Output: Water freezes at 0C and boils at 100C.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [exec, méthode \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match, méthode \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)   
 [search, méthode \(String\)](../../javascript/reference/search-method-string-javascript.md)   
 [test, méthode \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmation d'expression régulière \(scripts\)](http://msdn.microsoft.com/fr-fr/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternative et sous\-expressions \(scripts\)](http://msdn.microsoft.com/fr-fr/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Références arrière \(scripts\)](http://msdn.microsoft.com/fr-fr/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [Exemple d'application Glisser\-déplacer HTML5](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)