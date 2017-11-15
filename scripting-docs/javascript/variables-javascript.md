---
title: Variables (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- coercion
- case sensitivity, JavaScript variable name
ms.assetid: 12a450e5-4818-4a09-9878-cd7c6cd2a248
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f30946899ad35286dfb1e786cf903d58f5c98cb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="variables-javascript"></a>Variables (JavaScript)
Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], une variable contient une valeur, par exemple « hello » ou 5. Quand vous utilisez la variable, vous faites référence aux données qu’elle représente, par exemple `NumberOfDaysLeft = EndDate - TodaysDate`.  
  
 Les variables vous permettent de stocker, de récupérer et de manipuler des valeurs qui apparaissent dans votre code. Essayez de donner à vos variables des noms significatifs pour aider d’autres personnes à comprendre ce que fait votre code.  
  
## <a name="declaring-variables"></a>Déclaration de variables  
 La déclaration d’une variable correspond à la première apparition de la variable dans votre script. Elle est définie en mémoire pour que vous puissiez y faire référence par la suite dans votre script. Vous devez déclarer les variables avant de les utiliser. Pour cela, utilisez le mot clé `var`.  
  
```JavaScript  
// A single declaration.  
var count;    
// Multiple declarations with a single var keyword.  
var count, amount, level;      
// Variable declaration and initialization in one statement.  
var count = 0, amount = 100;   
```  
  
 Si vous n’initialisez pas votre variable dans l’instruction `var`, elle prend automatiquement la valeur `undefined`.  
  
## <a name="naming-variables"></a>Attribution de noms aux variables  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est un langage qui respecte la casse. Cela signifie qu’un nom de variable comme **Moncompteur** est différent du nom de variable **MONCompteur**. La longueur des noms de variable n’est pas limitée. Pour créer des noms de variable autorisés, tenez compte des règles suivantes :  
  
-   Le premier caractère doit être une lettre ASCII (majuscule ou minuscule) ou un trait de soulignement (_). Notez que le premier caractère ne peut pas être un nombre.  
  
-   Les caractères suivants doivent être des lettres, des chiffres ou des traits de soulignement (_).  
  
-   Le nom de la variable ne doit pas être un [mot réservé](../javascript/reference/javascript-reserved-words.md).  
  
 Voici quelques exemples de noms de variables valides :  
  
```  
_pagecount   
Part9   
Number_Items   
```  
  
 Voici quelques exemples de noms de variables non valides :  
  
```JavaScript  
// Cannot begin with a number.   
99Balloons     
// The ampersand (&) character is not a valid character for variable names.   
Alpha&Beta   
```  
  
 Si vous souhaitez déclarer une variable et l’initialiser, mais que vous ne souhaitez pas lui donner une valeur particulière, affectez-lui la valeur `null`. Voici un exemple :  
  
```JavaScript  
var bestAge = null;  
var muchTooOld = 3 * bestAge; // muchTooOld has the value 0.  
```  
  
 Si vous déclarez une variable sans lui affecter de valeur, elle a la valeur `undefined`. Voici un exemple :  
  
```JavaScript  
var currentCount;  
// finalCount has the value NaN because currentCount is undefined.  
var finalCount = 1 * currentCount;   
```  
  
 La valeur `null` se comporte comme le nombre 0, tandis que `undefined` se comporte comme la valeur spéciale `NaN` (pas un nombre). Si vous comparez une valeur `null` et une valeur `undefined`, elles sont égales.  
  
 Vous pouvez déclarer une variable sans utiliser le mot clé `var` dans la déclaration, puis lui attribuer une valeur. Il s’agit d’une déclaration implicite.  
  
```JavaScript  
// The variable noStringAtAll is declared implicitly.  
noStringAtAll = "";   
```  
  
 Vous ne pouvez pas utiliser une variable qui n’a jamais été déclarée.  
  
```JavaScript  
// Error. Length and width do not yet exist.  
var area = length * width;   
```  
  
## <a name="coercion"></a>Forçage de type  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] est un langage faiblement typé rapport à des langages fortement typés comme C++. Cela signifie que les variables JavaScript n’ont pas de type prédéterminé. Au lieu de cela, le type d’une variable est le type de sa valeur. Ce comportement vous permet de traiter une valeur comme si elle était d’un type différent.  
  
 Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], vous pouvez effectuer des opérations sur des valeurs de types différents sans provoquer d’exception. L’interpréteur [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] convertit implicitement les données d’un type à l’autre, ou *force le type*, puis effectue l’opération. Les règles de forçage de type pour les valeurs de type chaîne, nombre et booléen sont les suivantes :  
  
-   Si vous ajoutez un nombre et une chaîne, le nombre est forcé en chaîne.  
  
-   Si vous ajoutez un booléen et une chaîne, le booléen est forcé en chaîne.  
  
-   Si vous ajoutez un nombre et un booléen, le booléen est forcé en nombre.  
  
 Dans l’exemple suivant, un nombre ajouté à une chaîne produit une chaîne.  
  
```JavaScript  
var x = 2000;  
var y = "Hello";  
// The number is coerced to a string.  
x = x + y;  
document.write(x);   
  
// Output:  
// 2000Hello  
```  
  
 Les chaînes sont automatiquement converties en nombres équivalents à des fins de comparaison. Pour convertir explicitement une chaîne en entier, utilisez la [fonction parseInt](../javascript/reference/parseint-function-javascript.md). Pour convertir explicitement une chaîne en nombre, utilisez la [fonction parseFloat](../javascript/reference/parsefloat-function-javascript.md).