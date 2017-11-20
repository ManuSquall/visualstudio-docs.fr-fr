---
title: "Replace, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: replace
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- replacing strings
- Replace method
ms.assetid: 5f0e4765-df4d-4887-bd09-efe5e58251bf
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e78e17d4b9060a3a52498109a744c13cdf972abb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="replace-method-string-javascript"></a>replace, méthode (String) (JavaScript)
Remplace du texte dans une chaîne, à l'aide d'une expression régulière ou d'une chaîne de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
stringObj. replace(rgExp, replaceText)  
```  
  
## <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet `String` ou littéral de chaîne sur lequel effectuer le remplacement. Cette chaîne n’est pas modifiée par le **remplacer** (méthode). Au lieu de cela, la valeur de retour de cette méthode est la chaîne produite par le remplacement.  
  
 `rgExp`  
 Obligatoire. Une instance d’un **Expression régulière** objet qui contient le modèle d’expression régulière et les indicateurs applicables. Peut également être un objet `String` ou un littéral de chaîne qui représente l'expression régulière. Si `rgExp` n’est pas une instance d’un **Expression régulière** objet, il est converti en une chaîne et une recherche exacte est lancée ; aucune tentative est faite pour convertir la chaîne en une expression régulière.  
  
 `replaceText`  
 Obligatoire. Objet `String` ou littéral de chaîne contenant le texte de remplacement pour chaque correspondance trouvée de `rgExp` dans `stringObj`. Dans [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure, l'argument `replaceText` peut également être une fonction qui retourne le texte de remplacement.  
  
## <a name="return-value"></a>Valeur de retour  
 Le résultat de la **remplacer** (méthode) est une copie de `stringObj` une fois que les remplacements spécifiés ont été apportées.  
  
## <a name="remarks"></a>Remarques  
 Les variables de correspondance suivantes peuvent toutes être utilisées pour identifier la correspondance la plus récente ainsi que la chaîne où elle se situe. Ces variables peuvent être employées dans le texte de remplacement où la chaîne de remplacement doit être déterminée de façon dynamique.  
  
|Caractères|Signification|  
|----------------|-------------|  
|**$$**|`$` ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure)|  
|**$&**|Spécifie la partie de `stringObj` que l'ensemble du modèle a trouvée. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure)|  
|`$``|Spécifie la partie de `stringObj` qui précède la correspondance décrite par  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure)|  
|`$'`|Spécifie la partie de `stringObj` qui suit la correspondance décrite par  **$&** . ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure)|  
|`$`  ***n***|Le  *n* ième sous-correspondance capturée, où  *n*  est un chiffre décimal unique compris entre 1 et 9. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure)|  
|`$`  ***nn***|Le  *nn* ième sous-correspondance capturée, où  *nn*  est un nombre décimal à deux chiffres de 01 à 99. ([!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] ou version ultérieure)|  
  
 Si `replaceText` est une fonction, pour chaque sous-chaîne trouvée, la fonction est appelée par le code suivant *m* + 3 arguments où *m* est le nombre de parenthèses de capture situées à gauche du `rgExp`. Le premier argument correspond à la sous-chaîne trouvée. La prochaine *m* arguments suivants sont les captures résultant de la recherche. Argument *m* + 2 correspond au décalage dans `stringObj` où la correspondance s’est produite et l’argument *m* + 3 est `stringObj`. Le résultat est la valeur de chaîne obtenue après le remplacement de chaque sous-chaîne trouvée avec la valeur de retour correspondante de l'appel de fonction.  
  
 Le **remplacer** méthode met à jour les propriétés de l’élément global `RegExp` objet.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la **remplacer** méthode pour remplacer toutes les instances de « the » par « a ».  
  
```JavaScript  
var s = "the batter hit the ball with the bat";  
  
// Replace "the" with "a".  
var re = /the/g;  
var result = s.replace(re, "a");  
document.write(result);  
// Output: a batter hit a ball with a bat  
```  
  
 En outre, le **remplacer** méthode peut également remplacer des sous-expressions dans le modèle. L'exemple suivant permute chaque paire de mots dans la chaîne.  
  
```JavaScript  
  
var s = "The quick brown fox jumped over the lazy dog.";  
var re = /(\S+)(\s+)(\S+)/g;  
// Exchange each pair of words.  
var result = s.replace(re, "$3$2$1");  
document.write(result);  
  
// Output:  quick The fox brown over jumps lazy the dog.  
```  
  
 L'exemple suivant, qui fonctionne dans [!INCLUDE[jsv55textspecific](../../javascript/reference/includes/jsv55textspecific-md.md)] et les versions ultérieures, montre comment utiliser une fonction qui retourne le texte de remplacement. Il remplace toute instance d'un nombre suivi de « F » par une conversion en degrés Celsius.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet chaîne](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [EXEC, méthode (Regular Expression)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match, méthode (String)](../../javascript/reference/match-method-string-javascript.md)   
 [RegExp (objet)](../../javascript/reference/regexp-object-javascript.md)   
 [Search, méthode (String)](../../javascript/reference/search-method-string-javascript.md)   
 [test, méthode (Regular Expression)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programmation d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)   
 [Alternative et sous-expressions (JavaScript)](http://msdn.microsoft.com/en-us/c59dd3e8-7fee-493e-9123-065af1e651ae)   
 [Références arrière (JavaScript)](http://msdn.microsoft.com/en-us/5d8dbd5a-cd03-4548-850b-9d7bad2c839a)   
 [HTML5 glisser- déposer exemple d’application](http://code.msdn.microsoft.com/Drag-and-drop-e2701a72)