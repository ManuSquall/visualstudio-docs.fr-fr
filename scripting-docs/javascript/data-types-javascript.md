---
title: Types de données (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569759"
---
# <a name="data-types-javascript"></a>Types de données (JavaScript)
Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], il existe trois types de données principaux, deux types de données composites et deux types de données spéciaux.  
  
## <a name="primary-data-types"></a>Types de données principaux  
 Les types de données principaux (primitifs) sont :  
  
-   String  
  
-   Number  
  
-   Boolean  
  
## <a name="composite-data-types"></a>Types de données composites  
 Les types de données composites (références) sont :  
  
-   Object  
  
-   Array  
  
## <a name="special-data-types"></a>Types de données spéciaux  
 Les types de données spéciaux sont :  
  
-   Null  
  
-   Undefined  
  
## <a name="string-data-type"></a>Type de données string  
 Une valeur string est une chaîne de zéro ou plusieurs caractères Unicode (lettres, chiffres et signes de ponctuation). Vous utilisez le type de données string pour représenter du texte dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Pour inclure des littéraux de chaîne dans vos scripts, vous devez les placer entre guillemets simples ou doubles. Les guillemets doubles peuvent être contenus dans des chaînes mises entre guillemets simples, et les guillemets simples peuvent être contenus dans des chaînes mises entre guillemets doubles. Voici des exemples de chaînes :  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Notez que [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] n’a pas de type pour représenter un caractère unique. Pour représenter un caractère unique dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], vous devez créer une chaîne composée d’un seul caractère. Une chaîne qui contient zéro caractère ("") est une chaîne vide (de longueur nulle).  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fournit des séquences d'échappement que vous pouvez inclure dans des chaînes pour créer des caractères que vous ne pouvez pas taper directement. Par exemple, `\t` spécifie un caractère de tabulation. Pour plus d’informations, consultez [Caractères spéciaux](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Type de données number  
 Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], il n’existe aucune distinction entre les valeurs entières et à virgule flottante. Un nombre [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] peut être l’un ou l’autre (en interne, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] représente tous les nombres sous forme de valeurs à virgule flottante).  
  
### <a name="integer-values"></a>Valeurs entières  
 Les valeurs entières peuvent être des nombres entiers positifs, des nombres entiers négatifs et zéro. Elles peuvent être représentées en base 10 (décimal), en base 16 (hexadécimal) et en base 8 (octal). La plupart des nombres dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sont écrits au format décimal.  
  
 Vous désignez des entiers hexadécimaux (« hex ») en ajoutant le préfixe « 0x » (zéro et x&#124;X). Ils peuvent contenir uniquement les chiffres de 0 à 9 et les lettres de A à F (majuscules ou minuscules). Les lettres de A à F sont utilisées pour représenter, en un seul chiffre, 10 à 15 en base 10. Autrement dit, 0xF équivaut à 15, et 0x10 équivaut à 16.  
  
 Vous désignez des entiers octaux en leur attribuant le préfixe « 0 » (zéro). Ils peuvent contenir uniquement les chiffres de 0 à 7. Un nombre qui commence par un « 0 » et qui contient les chiffres « 8 » et/ou « 9 » est interprété comme un nombre décimal.  
  
 Les nombres hexadécimaux et octaux peuvent être négatifs, mais ils ne peuvent pas avoir de partie décimale et ne peuvent pas être écrits dans la notation scientifique (exponentielle).  
  
> [!NOTE]
>  À compter de [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], la [fonction parseInt](../javascript/reference/parseint-function-javascript.md) ne traite pas comme octale une chaîne ayant le préfixe « 0 ». Toutefois, quand vous n’utilisez pas la fonction `parseInt`, les chaînes avec le préfixe « 0 » peuvent quand même être interprétées comme octales.  
  
### <a name="floating-point-values"></a>Valeurs à virgule flottante  
 Les valeurs à virgule flottante peuvent être des nombres entiers avec une partie décimale. En outre, elles peuvent être exprimées en notation scientifique. Autrement dit, un « e » majuscule ou minuscule est utilisé pour représenter « dix à la puissance de ». [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] représente les nombres à l’aide de la norme IEEE 754 relative aux nombres à virgule flottante sur huit octets pour la représentation numérique. Cela signifie que vous pouvez écrire des nombres aussi grands que 1,79769x10<sup>308</sup> et aussi petit que 5x10<sup>-324</sup>. Un nombre qui contient une virgule décimale et un seul « 0 » avant la virgule décimale est interprété comme un nombre décimal à virgule flottante.  
  
 Notez qu’un nombre qui commence par « 0x » ou « 00 » et qui contient une virgule décimale génère une erreur. Voici quelques exemples de nombres [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Nombre|Description|Équivalent décimal|  
|------------|-----------------|------------------------|  
|.0001, 0.0001, 1e-4, 1.0e-4|Quatre nombres à virgule flottante équivalents.|0.0001|  
|3.45e2|Nombre à virgule flottante.|345|  
|45|Entier.|45|  
|0378|Entier. Bien qu’il ressemble à un nombre octal (il commence par un zéro), 8 n’est pas un chiffre octal valide ; ce nombre est donc traité comme un nombre décimal.|378|  
|0377|Entier octal. Notez que bien que sa valeur semble être seulement un de moins que le nombre précédent, sa valeur réelle est assez différente.|255|  
|0.0001|Nombre à virgule flottante. Bien que ce nombre commence par un zéro, il ne s’agit pas d’un nombre octal, car il contient une virgule décimale.|0.0001|  
|00.0001|Il s’agit d’une erreur. Les deux zéros initiaux marquent le nombre comme octal, mais les valeurs octales ne doivent pas comporter de partie décimale.|N/A (erreur du compilateur)|  
|0Xff|Entier hexadécimal.|255|  
|0x37CF|Entier hexadécimal.|14287|  
|0x3e7|Entier hexadécimal. Notez que le « e » n’est pas traité comme une puissance.|999|  
|0x3.45e2|Il s’agit d’une erreur. Les nombres hexadécimaux ne peuvent pas comporter de parties décimales.|N/A (erreur du compilateur)|  
  
 En outre, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contient des nombres avec des valeurs spéciales. Il s’agit de :  
  
-   NaN (n’est pas un nombre). Utilisé quand une opération mathématique est effectuée sur des données inappropriées, telles que des chaînes ou la valeur non définie.  
  
-   Infini positif. Utilisé quand un nombre positif est trop grand pour être représenté dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   Infini négatif. Utilisé quand un nombre négatif est trop grand pour être représenté dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   Zéro positif et négatif. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] établit une distinction entre le zéro positif et le zéro négatif.  
  
## <a name="boolean-data-type"></a>Type de données boolean  
 Tandis que les types de données string et number peuvent avoir une quantité presque illimitée de valeurs différentes, le type de données boolean ne peut en avoir que deux. Il s’agit des littéraux `true` et `false`. Une valeur boolean est une vérité : elle spécifie si la condition est vraie ou fausse.  
  
 Les comparaisons que vous effectuez dans vos scripts aboutissent toujours à un résultat boolean. Examinez la ligne de code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] suivante.  
  
```JavaScript  
y = (x == 2000);  
```  
  
 Ici, la valeur de la variable `x` est comparée au nombre 2000. Si elle est égale, le résultat de la comparaison est la valeur boolean **true**, qui est assignée à la variable `y`. Si `x` n’est pas égal à 2000, le résultat de la comparaison est la valeur boolean `false`.  
  
 Les valeurs boolean sont particulièrement utiles dans les structures de contrôle. Le code suivant combine une comparaison qui crée une valeur boolean directement avec une instruction qui l’utilise. Examinez l’exemple de code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] suivant :  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 L’instruction `if/else` dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] effectue une action si une valeur boolean est `true` (`z = z + 1`) et une autre action si la valeur boolean est `false` (`x = x + 1`).  
  
 Vous pouvez utiliser n’importe quelle expression comme expression de comparaison. Toute expression évaluée comme zéro, null, non défini ou une erreur de chaîne est interprétée comme `false`. Une expression évaluée à toute autre valeur est interprétée comme `true`. Par exemple, vous pouvez utiliser une expression telle que :  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Notez que la ligne ci-dessus ne vérifie pas si `x` est égal à `y + z`, car un seul signe égal (opérateur d’assignation) est utilisé. Au lieu de cela, le code ci-dessus assigne la valeur de `y + z` à la variable `x`, puis vérifie si le résultat de l’expression entière (la valeur de `x`) est zéro. Pour vérifier si `x` est égal à `y + z`, vous devez utiliser le code suivant.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Pour plus d’informations sur les comparaisons, consultez [Contrôle du flux de programme](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>Type de données null  
 Le type de données `null` a une seule valeur dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] : null. Vous ne pouvez pas utiliser le mot clé `null` comme nom d’une fonction ou d’une variable.  
  
 Une variable qui contient `null` ne contient aucune valeur number,string, boolean, array ou object valide. Vous pouvez effacer le contenu d’une variable (sans supprimer la variable) en lui assignant la valeur `null`.  
  
 Notez que dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` n’est pas la même chose que 0 (comme c’est le cas en C et C++). Notez également que l’opérateur `typeof` dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] signale les valeurs `null` comme étant de type `Object`, et non de type `null`. Ce comportement pouvant prêter à confusion est destiné à la compatibilité descendante.  
  
## <a name="the-undefined-data-type"></a>Type de données undefined  
 La valeur `undefined` est retournée quand vous utilisez une propriété d’objet qui n’existe pas, ou une variable qui a été déclarée mais à laquelle aucune valeur n’a jamais été assignée.  
  
 Vous pouvez vérifier si une variable existe en la comparant à `undefined`, bien que vous puissiez vérifier si son type est `undefined` en comparant le type de la variable à la chaîne « undefined ». L’exemple suivant montre comment savoir si la variable `x` a été déclarée :  
  
```JavaScript  
  
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
  
 Vous pouvez également comparer la valeur undefined à `null`. Cette comparaison est `true` si la propriété `someObject.prop` est `null` ou si la propriété `someObject.prop` n’existe pas.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Pour savoir si une propriété d’objet existe, vous pouvez utiliser l’opérateur **in** :  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objets et tableaux](../javascript/objects-and-arrays-javascript.md)   
 [Opérateur typeof](../javascript/reference/typeof-operator-decrementjavascript.md)