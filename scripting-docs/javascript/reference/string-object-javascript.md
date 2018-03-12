---
title: "Chaîne, objet (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- String_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object
- String object, overview
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d58f567bb301b29324fee8ed75fc95fd1a4791ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="string-object-javascript"></a>String, objet (JavaScript)
Permet de manipuler et mettre en forme des chaînes de texte, ainsi que de définir et placer des sous-chaînes à l'intérieur de chaînes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## <a name="parameters"></a>Paramètres  
 `newString`  
 Obligatoire. Nom de la variable à laquelle l'objet `String` est assigné.  
  
 `stringLiteral`  
 Facultatif. Tout groupe de caractères Unicode.  
  
## <a name="remarks"></a>Remarques  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fournit des séquences d'échappement que vous pouvez inclure dans des chaînes pour créer des caractères que vous ne pouvez pas taper directement. Par exemple, `\t` spécifie un caractère de tabulation. Pour plus d’informations, consultez [Caractères spéciaux](../../javascript/advanced/special-characters-javascript.md).  
  
## <a name="string-literals"></a>Littéraux de chaîne  
 A *littéral de chaîne* est zéro ou plusieurs caractères placés entourés guillemets simples ou doubles. Le type de données (primitif) principal d'un littéral de chaîne est `string`. A *objet String* est créé à l’aide de la [nouvel opérateur](../../javascript/reference/new-operator-decrementjavascript.md), et a un type de données `Object`.  
  
 L'exemple suivant montre que le type de données d'un littéral de chaîne n'est pas le même que celui d'un objet `String`.  
  
```JavaScript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## <a name="methods-for-string-literals"></a>Méthodes pour les littéraux de chaîne  
 Lorsque vous appelez une méthode sur un littéral de chaîne, il est temporairement converti en un objet de wrapper de chaîne. Le littéral de chaîne est traité comme si l'opérateur `new` était utilisé pour la créer.  
  
 L'exemple suivant applique la méthode `toUpperCase` à un littéral de chaîne.  
  
```JavaScript  
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
  
## <a name="accessing-an-individual-character"></a>Accès à un caractère individuel  
 Vous pouvez accéder à un caractère individuel d'une chaîne en tant que propriété en lecture seule indexée dans un tableau. Cette fonctionnalité a été introduite dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)]. L'exemple suivant accède à des caractères de chaîne individuels.  
  
```JavaScript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## <a name="requirements"></a>Spécifications  
 L'objet `String Object` a été introduit dans [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)]. Certains membres des listes suivantes ont été introduits dans les versions ultérieures.  
  
<a name="js56jsobjstringprop"></a>   
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `String`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-string.md)|Spécifie la fonction qui crée un objet.|  
|[Propriété length (Chaîne)](../../javascript/reference/length-property-string-javascript.md)|Retourne la longueur d'un objet `String`.|  
|[prototype, propriété](../../javascript/reference/prototype-property-string.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `String`.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonction String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Retourne une chaîne à partir d'un certain nombre de valeurs de caractères Unicode.|  
|[Fonction String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Retourne la chaîne associée avec un point de code Unicode UTF-16.|  
|[Fonction String.raw](../../javascript/reference/string-raw-function-javascript.md)|Retourne la chaîne brute d'une chaîne modèle.|  
  
<a name="js56jsobjstringmeth"></a>   
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `String`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode Anchor](../../javascript/reference/html-tag-methods-javascript.md)|Place un point d'ancrage HTML comprenant un attribut NAME autour du texte.|  
|[Méthode Big](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<BIG > autour du texte, les balises.|  
|[Méthode blink](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<BLINK > autour du texte, les balises.|  
|[Méthode bold](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<B > balises autour du texte.|  
|[Méthode charAt](../../javascript/reference/charat-method-string-javascript.md)|Retourne le caractère situé à l'index spécifié.|  
|[Méthode charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Retourne l'encodage Unicode du caractère spécifié.|  
|[codepointat, méthode](../../javascript/reference/codepointat-method-string-javascript.md)|Retourne le point de code d'un caractère Unicode UTF-16.|  
|[Méthode concat (Chaîne)](../../javascript/reference/concat-method-string-javascript.md)|Retourne une chaîne contenant la concaténation de deux chaînes fournies.|  
|[endsWith, méthode](../../javascript/reference/endswith-method-string-javascript.md)|Retourne une valeur booléenne qui indique si une chaîne ou sous-chaîne se termine par la chaîne passée.|  
|[Includes (méthode)](../../javascript/reference/includes-method-string-javascript.md)|Retourne une valeur booléenne qui indique si la chaîne passée est contenue dans l'objet String.|  
|[Méthode fixed](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<TT > autour du texte, les balises.|  
|[Méthode fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<police > balises avec un attribut COLOR autour du texte.|  
|[Méthode fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<police > balises avec un attribut SIZE autour du texte.|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[Méthode indexOf (chaîne)](../../javascript/reference/indexof-method-string-javascript.md)|Retourne la position du caractère où s'est produite la première occurrence d'une sous-chaîne à l'intérieur d'une chaîne.|  
|[isPrototypeOf, méthode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la chaîne prototype d'un autre objet.|  
|[Méthode italics](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<I > balises autour du texte.|  
|[Méthode lastIndexOf (Chaîne)](../../javascript/reference/lastindexof-method-string-javascript.md)|Retourne la dernière occurrence d'une sous-chaîne à l'intérieur d'une chaîne.|  
|[Méthode link](../../javascript/reference/html-tag-methods-javascript.md)|Place un point d'ancrage HTML comprenant un attribut HREF autour du texte.|  
|[méthode localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Retourne une valeur qui indique si deux chaînes sont équivalentes d'après les paramètres régionaux en cours.|  
|[Méthode match](../../javascript/reference/match-method-string-javascript.md)|Recherche une chaîne en utilisant un fourni **Expression régulière** de l’objet et retourne les résultats sous forme de tableau.|  
|[Normalize, méthode](../../javascript/reference/normalize-method-string-javascript.md)|Retourne le formulaire de normalisation Unicode d'une chaîne spécifiée.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne indiquant si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Repeat, méthode](../../javascript/reference/repeat-method-string-javascript.md)|Retourne un nouvel objet String avec une valeur égale à la chaîne d'origine répétée le nombre de fois spécifié.|  
|[Méthode replace](../../javascript/reference/replace-method-string-javascript.md)|Utilise une expression régulière pour remplacer du texte dans une chaîne et retourne le résultat.|  
|[Méthode search](../../javascript/reference/search-method-string-javascript.md)|Retourne la position de la première correspondance de sous-chaîne dans une recherche d'expression régulière.|  
|[Méthode slice (Chaîne)](../../javascript/reference/slice-method-string-javascript.md)|Retourne une section de chaîne.|  
|[Méthode small](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<SMALL > autour du texte, les balises.|  
|[Méthode split](../../javascript/reference/split-method-string-javascript.md)|Retourne le tableau de chaînes obtenu lorsqu'une chaîne est fractionnée en sous-chaînes.|  
|[StartsWith, méthode](../../javascript/reference/startswith-method-string-javascript.md)|Retourne une valeur booléenne qui indique si une chaîne ou sous-chaîne commence par la chaîne passée.|  
|[Méthode strike](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<STRIKE > autour du texte, les balises.|  
|[Méthode sub](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<SUB > balises autour du texte.|  
|[Méthode substr](../../javascript/reference/substr-method-string-javascript.md)|Retourne une sous-chaîne débutant à une position spécifiée et ayant une longueur déterminée.|  
|[Méthode substring](../../javascript/reference/substring-method-string-javascript.md)|Retourne une sous-chaîne débutant à la position spécifiée dans un objet `String`.|  
|[Méthode sup](../../javascript/reference/html-tag-methods-javascript.md)|Place la balise HTML \<SUP > balises autour du texte.|  
|[toLocaleLowerCase, méthode](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en minuscules, en fonction des paramètres régionaux définis pour l'environnement hôte.|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Retourne un objet converti en chaîne, à l'aide des paramètres régionaux actuels.|  
|[toLocaleUpperCase, méthode](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en majuscules, en fonction des paramètres régionaux définis pour l'environnement hôte.|  
|[Méthode toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en minuscules.|  
|[ToString, méthode](../../javascript/reference/tostring-method-string-1.md)|Retourne la chaîne.|  
|[Méthode toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Retourne une chaîne dans laquelle tous les caractères alphabétiques sont convertis en majuscules.|  
|[Méthode trim](../../javascript/reference/trim-method-string-javascript.md)|Retourne une chaîne dans laquelle les espaces blancs de début et de fin et les caractères de fin de ligne sont supprimés.|  
|[valueOf, méthode](../../javascript/reference/valueof-method-string.md)|Retourne la chaîne.|  
  
## <a name="see-also"></a>Voir aussi  
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Exemple d’application de défilement, panoramique et zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)