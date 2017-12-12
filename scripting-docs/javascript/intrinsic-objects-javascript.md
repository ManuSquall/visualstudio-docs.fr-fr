---
title: "Objets intrinsèques (JavaScript) | Microsoft Docs"
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
- built-in objects [JavaScript]
- intrinsic objects [JavaScript]
ms.assetid: 6520c634-a7d1-4a05-8c1b-2e79f449d2e4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242b572c2818f9968e6d5fc51e1272e3004c0f05
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="intrinsic-objects-javascript"></a>Objets intrinsèques (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fournit des objets intrinsèques (ou « intégrés »). Il s’agit des objets `Array`, `Boolean`, `Date`, `Error`, `Function`, **Global**, **JSON**, **Math**, **Number**, `Object`, `RegExp` et `String`. Les objets intrinsèques ont des méthodes, des fonctions, des propriétés et des constantes associées qui sont décrites en détail dans la [référence du langage](../javascript/reference/javascript-reference.md).  
  
## <a name="array-object"></a>Objet Array  
 Les indices d'un tableau peuvent être considérés comme les propriétés d'un objet et sont désignés par leur index numérique. Notez que les propriétés nommées ajoutées à un tableau ne peuvent pas être indexées par nombre ; elles sont séparées des éléments de tableau.  
  
 Pour créer un tableau, utilisez l’opérateur **new** et le [constructeur](../javascript/reference/constructor-property-object-javascript.md) **Array()**, comme dans l’exemple suivant.  
  
```JavaScript  
var theMonths = new Array(12);  
theMonths[0] = "Jan";  
theMonths[1] = "Feb";  
theMonths[2] = "Mar";  
theMonths[3] = "Apr";  
theMonths[4] = "May";  
theMonths[5] = "Jun";  
theMonths[6] = "Jul";  
theMonths[7] = "Aug";  
theMonths[8] = "Sep";  
theMonths[9] = "Oct";  
theMonths[10] = "Nov";  
theMonths[11] = "Dec";  
```  
  
 Quand vous créez un tableau à l’aide du mot clé `Array`, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] inclut une propriété **length** qui enregistre le nombre d’entrées. Si vous ne spécifiez pas de nombre, la longueur est définie à la valeur 0 et le tableau ne comporte aucune entrée. Si vous spécifiez un nombre, il détermine la longueur. Si vous spécifiez plusieurs paramètres, ces derniers sont utilisés comme entrées du tableau. De plus, le nombre de paramètres est assigné à la propriété length comme dans l'exemple suivant, qui équivaut à l'exemple précédent.  
  
```JavaScript  
var theMonths = new Array("Jan", "Feb", "Mar", "Apr", "May", "Jun",   
"Jul", "Aug", "Sep", "Oct", "Nov", "Dec");  
```  
  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] modifie automatiquement la valeur de **length** quand vous ajoutez des éléments à un tableau que vous avez créé avec le mot clé `Array`. Les index de tableau de [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] commencent toujours à 0, jamais à 1, de sorte que la propriété length est toujours supérieure de un à l'index le plus élevé du tableau.  
  
## <a name="string-object"></a>Objet String  
 Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], vous pouvez traiter des chaînes (et des nombres) comme des objets. [L’objet String](../javascript/reference/string-object-javascript.md) a certaines méthodes intégrées que vous pouvez utiliser avec vos chaînes. L’une d’entre elles est la [méthode substring](../javascript/reference/substring-method-string-javascript.md), qui retourne une partie de la chaîne. Elle utilise deux nombres comme arguments.  
  
```JavaScript  
var aString = "0123456789";  
  
// This code sets aChunk to "456".  
var aChunk = aString.substring(4, 7);  
  
// This code sets anotherChunk to "456", using  
// the lower value index as the starting index.  
var anotherChunk = aString.substring(7, 4);  
  
// This code sets the firstLetter variable to "J"  
// by using the array in the preceding array creation example.  
firstLetter = theMonths[5].substring(0,1);  
```  
  
 Une autre propriété de l’objet `String` est la propriété **length**. Cette propriété contient le nombre de caractères de la chaîne (0 pour une chaîne vide). Il s'agit d'une valeur numérique qui peut être utilisée directement dans les calculs.  
  
```JavaScript  
var howLong = "Hello World".length  // Sets the howLong variable to 11.  
```  
  
## <a name="math-object"></a>Objet Math  
 L’objet **Math** a plusieurs constantes et fonctions prédéfinies. Les constantes sont des nombres spécifiques. L'un de ces nombres est la valeur de pi (environ 3,14159...). Il s’agit de la constante **Math.PI**, illustrée dans l’exemple suivant.  
  
```JavaScript  
var radius = 5;  
var circleArea = Math.PI * radius * radius;  
```  
  
 L’une des fonctions intégrées de l’objet **Math** est la méthode d’élévation, ou `Math.pow`, qui élève un nombre à une puissance spécifiée. L'exemple suivant utilise à la fois pi et l'élévation à une puissance pour calculer le volume d'une sphère.  
  
```JavaScript  
var volume = (4/3)*(Math.PI*Math.pow(radius,3));  
```  
  
## <a name="date-object"></a>Objet Date  
 L'objet `Date` peut être utilisé pour représenter des dates et heures arbitraires, pour obtenir la date système actuelle et pour calculer les différences entre les dates. Il comporte plusieurs propriétés et méthodes prédéfinies. Généralement, l'objet `Date` fournit le jour de la semaine ; le mois, le jour et l'année ; et l'heure en heures, minutes et secondes. Ces informations sont basées sur le nombre de millisecondes écoulées depuis le 1er janvier 1970, 00:00:000 GMT. GMT correspond à l'heure de Greenwich (GMT, Greenwich Mean Time) (le terme par défaut est l'heure UTC, ou « Universal Coordinated Time », qui fait référence à des signaux émis par la norme du temps universel). [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] peut gérer des dates qui se trouvent dans la plage approximative de 250 000 avant J.-C. à 255 000 ans après J.-C.  
  
 Pour créer un objet `Date`, utilisez l’opérateur **new**, comme illustré dans l’exemple suivant.  
  
```JavaScript  
var toDay = new Date();    
var thisYear = toDay.getFullYear();  
var thisMonth = theMonths[toDay.getMonth()];  
var thisDay = thisMonth  + " " + toDay.getDate() + ", " + thisYear;  
```  
  
## <a name="number-object"></a>Objet Number  
 Outre les constantes numériques spéciales (`PI`, par exemple) disponibles dans l’objet **Math**, plusieurs autres constantes sont disponibles dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] par le biais de l’objet **Number**.  
  
|Constante|Description|  
|--------------|-----------------|  
|Number.MAX_VALUE|Plus grand nombre possible, soit environ 1.79E+308 ; peut être positif ou négatif. (Cette valeur varie légèrement d'un système à un autre.)|  
|Number.MIN_VALUE|Plus petit nombre possible, soit environ 5.00E-324 ; peut être positif ou négatif. (Cette valeur varie légèrement d'un système à un autre.)|  
|Number.NaN|Valeur non numérique spéciale ; signifie « not a number (pas un nombre) ». |  
|Number.POSITIVE_INFINITY|Toute valeur positive supérieure au plus grand nombre possible (Number.MAX_VALUE) est automatiquement convertie en cette valeur ; représentée comme l'infini.|  
|Number.NEGATIVE_INFINITY|Toute valeur plus négative que le plus grand nombre négatif possible (-Number.MAX_VALUE) est automatiquement convertie en cette valeur ; représentée comme -l'infini.|  
  
 **Number.NaN** est une constante spéciale définie comme « not a number (pas un nombre) ». Une tentative d’analyse d’une chaîne qui ne peut pas être analysée comme un nombre retourne **Number.NaN**. `NaN` n'équivaut à aucun nombre ni à lui-même quand il est comparé. Pour tester un résultat `NaN`, n’effectuez pas la comparaison par rapport à **Number.NaN** ; utilisez plutôt la fonction **isNaN()**.  
  
## <a name="json-object"></a>Objet JSON  
 JSON est un format d’échange de données léger basé sur un sous-ensemble de la notation de littéral d’objet du langage JavaScript.  
  
 L'objet JSON fournit deux fonctions permettant de convertir vers et depuis le format de texte JSON. La fonction [JSON.stringify](../javascript/reference/json-stringify-function-javascript.md) sérialise les objets et les tableaux en texte JSON. La fonction [JSON.parse](../javascript/reference/json-parse-function-javascript.md) désérialise le texte JSON pour produire des objets en mémoire. Pour plus d'informations, consultez [Introduction à JSON (JavaScript Object Notation) dans JavaScript et .NET](http://go.microsoft.com/fwlink/?LinkId=124098).  
  
## <a name="see-also"></a>Voir aussi  
 [Objets JavaScript](../javascript/reference/javascript-objects.md)