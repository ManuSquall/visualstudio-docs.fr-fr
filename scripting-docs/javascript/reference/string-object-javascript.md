---
title: "String, objet (JavaScript) | Microsoft Docs"
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
  - "String_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String (objet)"
  - "String (objet), vue d'ensemble"
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# String, objet (JavaScript)
Permet de manipuler et mettre en forme des chaînes de texte, ainsi que de définir et placer des sous\-chaînes à l'intérieur de chaînes.  
  
## Syntaxe  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## Paramètres  
 `newString`  
 Obligatoire.  Nom de la variable à laquelle l'objet `String` est assigné.  
  
 `stringLiteral`  
 Facultatif.  Groupe de caractères Unicode.  
  
## Notes  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fournit des séquences d'échappement que vous pouvez inclure dans les chaînes pour créer des caractères que vous ne pouvez pas taper directement.  Par exemple, `\t` spécifie un caractère de tabulation.  Pour plus d'informations, consultez [Caractères spéciaux](../../javascript/advanced/special-characters-javascript.md)  
  
## Littéraux de chaîne  
 Un *littéral de chaîne* consiste en zéro, un ou plusieurs caractères placés entre des guillemets simples ou doubles.  Le type de données principal \(primitif\) d'un littéral de chaîne est `string`.  Un *objet String* est créé à l'aide de l'[opérateur new](../../javascript/reference/new-operator-decrementjavascript.md) et son type de données est `Object`.  
  
 L'exemple suivant montre que le type de données d'un littéral de chaîne n'est pas le même que celui d'un objet `String`.  
  
```javascript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## Méthodes pour les littéraux de chaîne  
 Quand vous appelez une méthode sur un littéral de chaîne, il est temporairement converti en un objet de wrapper de chaîne.  Le littéral de chaîne est traité comme si l'opérateur `new` était utilisé pour le créer.  
  
 L'exemple suivant applique la méthode `toUpperCase` à un littéral de chaîne.  
  
```javascript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## Accès à un caractère individuel  
 Vous pouvez accéder à un caractère individuel d'une chaîne en tant que propriété en lecture seule indexée dans un tableau.  Cette fonctionnalité a été introduite dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  L'exemple suivant accède à des caractères de chaîne individuels.  
  
```javascript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## Configuration requise  
 L'objet `String Object` était une nouveauté d'[!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Certains membres des listes suivantes ont été introduits dans les versions ultérieures.  
  
<a name="js56jsobjstringprop"></a>   
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `String`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété constructor](../../javascript/reference/constructor-property-string.md)|Spécifie la fonction qui crée un objet.|  
|[Propriété length \(String\)](../../javascript/reference/length-property-string-javascript.md)|Retourne la longueur d'un objet `String`.|  
|[Propriété prototype](../../javascript/reference/prototype-property-string.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `String`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonction String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Retourne une chaîne à partir d'un certain nombre de valeurs de caractères Unicode.|  
|[Fonction String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Retourne la chaîne associée à un point de code Unicode UTF\-16.|  
|[Fonction String.raw](../../javascript/reference/string-raw-function-javascript.md)|Retourne la forme de chaîne brute d'une chaîne de modèle.|  
  
<a name="js56jsobjstringmeth"></a>   
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `String`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode anchor](../../javascript/reference/html-tag-methods-javascript.md)|Place un point d'ancrage HTML comprenant un attribut NAME autour du texte.|  
|[Méthode big](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<BIG\> autour du texte.|  
|[Méthode blink](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<BLINK\> autour du texte.|  
|[Méthode bold](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<B\> autour du texte.|  
|[Méthode charAt](../../javascript/reference/charat-method-string-javascript.md)|Retourne le caractère situé à l'index spécifié.|  
|[Méthode charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Retourne l'encodage Unicode du caractère spécifié.|  
|[Méthode codePointAt](../../javascript/reference/codepointat-method-string-javascript.md)|Retourne le point de code d'un caractère Unicode UTF\-16.|  
|[Méthode concat \(String\)](../../javascript/reference/concat-method-string-javascript.md)|Retourne une chaîne contenant la concaténation de deux chaînes fournies.|  
|[Méthode endsWith](../../javascript/reference/endswith-method-string-javascript.md)|Retourne une valeur booléenne qui indique si une chaîne ou sous\-chaîne se termine par la chaîne passée.|  
|[Méthode includes](../../javascript/reference/includes-method-string-javascript.md)|Retourne une valeur booléenne qui indique si la chaîne passée est contenue dans l'objet String.|  
|[Méthode fixed](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<TT\> autour du texte.|  
|[Méthode fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<FONT\> avec un attribut COLOR autour du texte.|  
|[Méthode fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<FONT\> avec un attribut SIZE autour du texte.|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[Méthode indexOf \(String\)](../../javascript/reference/indexof-method-string-javascript.md)|Retourne la position du caractère où s'est produite la première occurrence d'une sous\-chaîne à l'intérieur d'une chaîne.|  
|[Méthode isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la chaîne prototype d'un autre objet.|  
|[Méthode italics](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<I\> autour du texte.|  
|[Méthode lastIndexOf \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)|Retourne la dernière occurrence d'une sous\-chaîne à l'intérieur d'une chaîne.|  
|[Méthode link](../../javascript/reference/html-tag-methods-javascript.md)|Place un point d'ancrage HTML comprenant un attribut HREF autour du texte.|  
|[Méthode localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Retourne une valeur qui indique si deux chaînes sont équivalentes d'après les paramètres régionaux actuels.|  
|[Méthode match](../../javascript/reference/match-method-string-javascript.md)|Recherche une chaîne en utilisant un objet **Regular Expression** fourni et retourne les résultats sous la forme d'un tableau.|  
|[Méthode normalize](../../javascript/reference/normalize-method-string-javascript.md)|Retourne le formulaire de normalisation Unicode d'une chaîne spécifiée.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne qui indique si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Méthode repeat](../../javascript/reference/repeat-method-string-javascript.md)|Retourne un nouvel objet String avec une valeur égale à la chaîne d'origine répétée le nombre de fois spécifié.|  
|[Méthode replace](../../javascript/reference/replace-method-string-javascript.md)|Utilise une expression régulière pour remplacer du texte dans une chaîne et retourne le résultat.|  
|[Méthode search](../../javascript/reference/search-method-string-javascript.md)|Retourne la position de la première correspondance de sous\-chaîne dans une recherche d'expression régulière.|  
|[Méthode slice \(String\)](../../javascript/reference/slice-method-string-javascript.md)|Retourne une section de chaîne.|  
|[Méthode small](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<SMALL\> autour du texte.|  
|[Méthode split](../../javascript/reference/split-method-string-javascript.md)|Retourne le tableau de chaînes obtenu quand une chaîne est fractionnée en sous\-chaînes.|  
|[Méthode startsWith](../../javascript/reference/startswith-method-string-javascript.md)|Retourne une valeur booléenne qui indique si une chaîne ou sous\-chaîne commence par la chaîne passée.|  
|[Méthode strike](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<STRIKE\> autour du texte.|  
|[Méthode sub](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<SUB\> autour du texte.|  
|[Méthode substr](../../javascript/reference/substr-method-string-javascript.md)|Retourne une sous\-chaîne commençant à un emplacement spécifié et ayant une longueur déterminée.|  
|[Méthode substring](../../javascript/reference/substring-method-string-javascript.md)|Retourne la sous\-chaîne à un emplacement spécifié dans un objet `String`.|  
|[Méthode sup](../../javascript/reference/html-tag-methods-javascript.md)|Place des balises HTML \<SUP\> autour du texte.|  
|[Méthode toLocaleLowerCase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en minuscules, en fonction des paramètres régionaux définis pour l'environnement hôte.|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retourne un objet converti en chaîne, à l'aide des paramètres régionaux actuels.|  
|[Méthode toLocaleUpperCase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en majuscules, en fonction des paramètres régionaux définis pour l'environnement hôte.|  
|[Méthode toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en minuscules.|  
|[Méthode toString](../../javascript/reference/tostring-method-string-1.md)|Retourne la chaîne.|  
|[Méthode toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en majuscules.|  
|[Méthode trim](../../javascript/reference/trim-method-string-javascript.md)|Retourne une chaîne dans laquelle les espaces de début et de fin ainsi que la marque de fin de ligne sont supprimés.|  
|[Méthode valueOf](../../javascript/reference/valueof-method-string.md)|Retourne la chaîne.|  
  
## Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Exemple d'application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)