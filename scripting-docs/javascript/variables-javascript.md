---
title: "Variables (JavaScript) | Microsoft Docs"
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
  - "respect de la casse, noms de variables JavaScript"
  - "contrainte"
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Variables (JavaScript)
En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], une variable contient une valeur, telle que « hello » ou 5.  Lorsque vous utilisez la variable, vous faites référence aux données qu'elle représente, par exemple `NumberOfDaysLeft = EndDate – TodaysDate`.  
  
 Vous utilisez des variables pour stocker, récupérer et manipuler les valeurs qui s'affichent dans votre code.  Essayez d'attribuer à vos variables des noms explicites afin que les autres personnes puissent comprendre facilement les opérations réalisées par votre code.  
  
## Déclaration de variables  
 La première apparition d'une variable dans votre script correspond à sa déclaration.  La première mention de la variable la place dans la mémoire, afin que vous puissiez vous y référer ultérieurement dans votre script.  Vous devez déclarer les variables avant de les utiliser.  Pour cela, utilisez le mot clé `var`.  
  
```javascript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Si vous n'initialisez pas votre variable dans l'instruction `var`, elle prend automatiquement la valeur `undefined`.  
  
## Attribution de noms aux variables  
 Le langage [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] respecte la casse.  Cela signifie qu'un nom de variable tel que myCounter est différent du nom de variable MYCounter.  Les noms des variables peuvent avoir n'importe quelle longueur.  En revanche, ils doivent respecter certaines conventions :  
  
-   Le premier caractère doit être une lettre ASCII \(majuscule ou minuscule\) ou un trait de soulignement \(\_\).  Notez qu'il n'est pas possible d'utiliser un chiffre comme premier caractère.  
  
-   Les caractères suivants doivent être des lettres, des chiffres ou des traits de soulignement \(\_\).  
  
-   Un nom de variable ne doit pas être un [mot réservé](../javascript/reference/javascript-reserved-words.md).  
  
 Voici quelques exemples de noms de variables valides :  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Voici quelques exemples de noms de variables non valides :  
  
```javascript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Lorsque vous voulez déclarer une variable et l'initialiser sans lui attribuer de valeur particulière, assignez\-lui la valeur `null`.  Voici un exemple.  
  
```javascript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Si vous déclarez une variable sans lui assigner de valeur, elle a la valeur `undefined`.  Voici un exemple.  
  
```javascript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 La valeur `null` se comporte comme le chiffre 0, tandis qu'`undefined` se comporte comme la valeur spéciale `NaN` \(Not a Number, pas un nombre\).  Si vous comparez une valeur `null` et une valeur `undefined`, elles sont égales.  
  
 Vous pouvez déclarer une variable sans utiliser le mot clé `var` dans la déclaration, et lui assigner une valeur.  Il s'agit d'une déclaration implicite.  
  
```javascript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Vous ne pouvez pas utiliser une variable n'ayant jamais été déclarée.  
  
```javascript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## Contrainte  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est un langage faiblement typé, par opposition aux langages fortement typés tels que C\+\+.  Cela signifie que les variables JavaScript n'ont pas de type prédéterminé.  À la place, le type d'une variable est le type de sa valeur.  Ce comportement vous permet de traiter une valeur comme s'il elle était d'un autre type.  
  
 En [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], vous pouvez effectuer des opérations sur des valeurs de différents types sans lever d'exception.  L'interpréteur [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] convertit implicitement, ou *force*, l'un des types de données dans celui de l'autre, puis effectue l'opération.  Les règles de contrainte des valeurs de chaîne, numériques et booléennes sont les suivantes :  
  
-   Si vous ajoutez un nombre et une chaîne, le nombre est converti en chaîne.  
  
-   Si vous ajoutez une valeur booléenne et une chaîne, la valeur booléenne est convertie en chaîne.  
  
-   Si vous ajoutez un nombre et une valeur booléenne, la valeur booléenne est convertie en nombre.  
  
 Dans l'exemple suivant, un nombre ajouté à une chaîne produit une chaîne.  
  
```javascript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Les chaînes sont automatiquement converties en nombres équivalents à des fins de comparaison.  Pour convertir explicitement une chaîne en entier, utilisez la [fonction parseInt](../javascript/reference/parseint-function-javascript.md).  Pour convertir explicitement une chaîne en nombre, utilisez la [fonction parseFloat](../javascript/reference/parsefloat-function-javascript.md).