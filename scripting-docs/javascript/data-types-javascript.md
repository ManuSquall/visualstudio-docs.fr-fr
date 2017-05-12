---
title: "Types de donn&#233;es (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "booléen (type de données), types de données prises en charge"
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Types de donn&#233;es (JavaScript)
Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], il existe trois types de données principales, deux types de données composite et deux types de données spéciaux.  
  
## Types de données principales  
 Les types de données principales \(primitives\) sont :  
  
-   Chaîne  
  
-   Numéro  
  
-   Boolean  
  
## Types de données composites  
 Les types de données composites \(référence\) sont :  
  
-   Objet  
  
-   Tableau  
  
## Types de données spéciaux  
 Les types de données spéciaux sont :  
  
-   Null  
  
-   Indéfini  
  
## Type de données String  
 Une valeur de chaîne est une suite de zéro, un ou plusieurs caractères Unicode \(lettres, chiffres et signes de ponctuation\).  Le type de données String est utilisé pour représenter du texte dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Vous incluez des littéraux de chaîne dans vos scripts en les encadrant par des guillemets simples ou doubles.  Des guillemets doubles peuvent être contenus dans des chaînes mises entre guillemets simples, et à l'inverse, des guillemets simples peuvent être contenus dans des chaînes mises entre guillemets doubles.  Voici des exemples de chaînes :  
  
```javascript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Notez que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ne possède pas de type pour représenter un caractère unique.  Pour représenter un caractère unique dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], créez une chaîne composée d'un seul caractère.  Une chaîne ne contenant aucun caractère \(""\) est une chaîne vide \(de longueur zéro\).  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fournit des séquences d'échappement que vous pouvez inclure dans des chaînes pour créer des caractères que vous ne pouvez pas taper directement.  Par exemple, `\t` spécifie une tabulation.  Pour plus d'informations, consultez [Caractères spéciaux](../javascript/advanced/special-characters-javascript.md).  
  
## Number, type de données  
 Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], il n'y a pas de distinction entre l'entier et les valeurs à virgule flottante ; un nombre [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] peut être soit l'un, soit l'autre \(en interne, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] représente tous les nombres comme des valeurs à virgule flottante\).  
  
### Valeurs entières  
 Une valeur entière peut être un nombre entier positif ou négatif, et 0.  Ils peuvent être représentés en base 10 \(décimale\), en base 16 \(hexadécimale\) et en base 8 \(octale\).  La plupart des nombres sont écrits au format décimal dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Vous désignez les entiers hexadécimaux \(hex\) à l'aide du préfixe « 0x » \(zéro et x&#124;X\).  Ils peuvent contenir les chiffres compris entre 0 et 9, ainsi que les lettres A à F \(en majuscules ou minuscules\).  Les lettres de A à F servent à représenter, sous forme de chiffres uniques, les nombres 10 à 15 en base 10.  Autrement dit, 0xF équivaut à 15 et 0x10 à 16.  
  
 Vous désignez les entiers en base octale à l'aide du préfixe 0 \(zéro\).  Ils peuvent uniquement contenir des chiffres compris entre 0 et 7.  Un nombre ayant 0 comme préfixe, mais contenant les chiffres 8 et\/ou 9 est interprété comme un nombre décimal.  
  
 Les nombres octaux et hexadécimaux peuvent être négatifs, mais ne peuvent pas comporter de partie décimale. De plus, ils ne peuvent pas être écrits en notation scientifique \(exponentiel\).  
  
> [!NOTE]
>  À partir de [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], la [fonction parseInt](../javascript/reference/parseint-function-javascript.md) ne traite pas une chaîne qui a un préfixe « 0 » comme octal.  Lorsque la fonction `parseInt` n'est pas utilisée, les chaînes ayant comme préfixe « 0 » peuvent toutefois être interprétées comme un entier de base octal.  
  
### Valeurs à virgule flottante  
 Les valeurs à virgule flottante sont des nombres entiers avec une partie décimale.  De plus, elles peuvent être exprimées en notation scientifique.  Cela signifie que la lettre « e » majuscule ou minuscule est utilisée pour représenter « fois dix à la puissance de ».  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] représente des nombres à l'aide du standard en virgule flottante IEEE 754 \(huit octets\) pour la représentation numérique.  Cela signifie qu'il est possible de saisir des nombres aussi grands que 1,79769x10<sup>308</sup> et aussi petits que 5x10<sup>-324</sup>.  Un nombre qui contient une virgule décimale et un « 0 » unique avant la virgule est interprété comme un nombre à virgule flottante décimal.  
  
 Notez qu'un nombre commençant par « 0x » ou « 00 » et contenant une virgule décimale génère une erreur.  Voici quelques exemples de nombres [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Numéro|Description|Équivalent décimal|  
|------------|-----------------|------------------------|  
|.0001, 0.0001, 1e\-4, 1.0e\-4|Quatre nombres à virgule flottante, tous équivalents.|0.0001|  
|3.45e2|Nombre à virgule flottante.|345|  
|45|Entier.|45|  
|0378|Entier.  Bien que ce nombre ressemble à un nombre en base octale \(il commence par zéro\), 8 n'est pas un chiffre octal valide ; aussi ce nombre est\-il traité comme nombre décimal.|378|  
|0377|Entier octal.  Notez que même si, à première vue, ce nombre semble différer d'une unité seulement par rapport au nombre précédent, sa valeur réelle est assez différente.|255|  
|0.0001|Nombre à virgule flottante.  Bien que ce nombre commence par zéro, il ne s'agit pas d'un nombre octal car il comporte une virgule décimale.|0.0001|  
|00.0001|Erreur.  Les deux zéros placés au début marquent le nombre comme un nombre octal, mais les nombres octaux ne sont pas autorisés dans un composant décimal.|Néant \(erreur du compilateur\)|  
|0Xff|Entier hexadécimal.|255|  
|0x37CF|Entier hexadécimal.|14287|  
|0x3e7|Entier hexadécimal.  Notez que la lettre « e » n'est pas considérée comme une puissance.|999|  
|0x3.45e2|Erreur.  Les nombres hexadécimaux ne peuvent pas comporter de parties décimales.|Néant \(erreur du compilateur\)|  
  
 De plus, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contient des nombres avec des valeurs spéciales.  Il s'agit des valeurs suivantes :  
  
-   NaN \(pas un nombre\).  Utilisé lorsqu'une opération mathématique est effectuée sur des données inappropriées, par exemple des chaînes ou la valeur undefined  
  
-   Infini positif.  Utilisé lorsqu'un nombre positif est trop grand pour être représenté dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Infini négatif.  Utilisé lorsqu'un nombre négatif est trop grand pour être représenté dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Zéro \(0\) positif ou négatif.  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] distingue le zéro positif du zéro négatif.  
  
## Type de données booléen  
 Alors que les types de données numériques et de chaîne peuvent théoriquement présenter un nombre illimité de valeurs différentes, le type de données booléen n'en reconnaît que deux.  Il y a les littéraux `true` et `false`.  Une valeur booléenne est une valeur de vérité : elle spécifie si la condition est true ou non.  
  
 Le résultat des comparaisons effectuées dans vos scripts est toujours une valeur booléenne.  Observons la ligne de code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] suivante :  
  
```javascript  
y = (x == 2000);  
```  
  
 Ici, la valeur de la variable `x` est comparée au nombre 2000.  Si tel est le cas, le résultat de la comparaison est la valeur booléenne **true**, qui est assignée à la variable `y`.  Si `x` n'est pas égal à 2000, la comparaison retourne comme résultat la valeur booléenne `false`.  
  
 Les valeurs booléennes sont particulièrement utiles dans les structures de contrôle.  Le code suivant combine une comparaison qui crée directement une valeur booléenne utilisée par une instruction.  Prenons l'exemple de code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] suivant.  
  
```javascript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 L'instruction `if/else` dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] exécute une action si une valeur booléenne a la valeur `true` \(`z = z + 1`\) et une autre action si la valeur booléenne a la valeur `false` \(`x = x + 1`\).  
  
 Vous pouvez utiliser une expression telle qu'une expression comparative.  Toute expression dont la valeur est 0, null, undefined ou dont la chaîne est vide est interprétée comme `false`.  Une expression qui correspond à toute autre valeur est interprétée comme `true`.  Par exemple, vous pouvez utiliser l'expression suivante :  
  
```javascript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Notez que la ligne ci\-dessus ne vérifie pas si `x` est égal à `y + z`, étant qu'un seul signe égal \(l'opérateur d'assignation\) est utilisé.  En revanche, le code ci\-dessus assigne la valeur de `y + z` à la variable `x`, puis vérifie si le résultat de l'expression entière \(la valeur de `x`\) est zéro.  Pour vérifier si `x` est égal à `y + z`, vous devez utiliser le code suivant.  
  
```javascript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Pour plus d'informations sur les comparaisons, consultez [Contrôle du flux du programme](../javascript/controlling-program-flow-javascript.md).  
  
## Type de données null  
 Le type de données `null` n'a qu'une seule valeur dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] : Null.  Le mot clé `null` ne peut pas être utilisé comme nom de fonction ou de variable.  
  
 Une variable contenant `null` ne contient aucun nombre, chaîne, valeur booléenne, tableau ou objet valide.  Pour effacer le contenu d'une variable \(sans supprimer la variable elle\-même\), vous pouvez lui assigner la valeur `null`.  
  
 Notez que dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` n'est pas identiques à 0 \(comme c'est le cas dans C et C\+\+\).  Notez également que l'opérateur `typeof` de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] considère les valeurs `null` comme étant du type `Object` et non du type `null`.  Ce comportement peut vous sembler déroutant, mais il est nécessaire pour des raisons de compatibilité descendante.  
  
## Type de données non défini  
 La valeur `undefined` est retournée lorsque vous utilisez une propriété d'objet qui n'existe pas, ou une variable qui a été déclarée, mais à qui aucune valeur n'a été affectée.  
  
 vous pouvez vérifier si une variable existe en la comparant à `undefined`, même si vous pouvez vérifier si son type est `undefined` en comparant le type de la variable à la chaîne « undefined ».  L'exemple suivant montre comment savoir si la variable `x` a été déclarée :  
  
```javascript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 Vous pouvez également comparer la valeur indéfinie à `null`.  Cette comparaison a la valeur `true` si la propriété `someObject.prop` a la valeur `null` ou si la propriété `someObject.prop` n'existe pas.  
  
```javascript  
someObject.prop == null;  
```  
  
 Pour déterminer si une propriété d'objet existe, vous pouvez utiliser l'opérateur **in**  :  
  
```javascript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## Voir aussi  
 [Objets et tableaux](../javascript/objects-and-arrays-javascript.md)   
 [typeof, opérateur](../javascript/reference/typeof-operator-decrementjavascript.md)