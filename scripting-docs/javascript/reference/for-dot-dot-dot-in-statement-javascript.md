---
title: "instruction for... dans l’instruction (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="forin-statement-javascript"></a>Instruction for...in (JavaScript)
Exécute une ou plusieurs instructions pour chaque propriété d’un objet ou chaque élément d’un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Paramètres  
 `variable`  
 Obligatoire. Une variable qui peut être n’importe quel nom de propriété de `object` ou un index de l’élément d’un `array`.  
  
 `object`, `array`  
 Facultatif. Un objet ou un tableau sur lequel vous souhaitez effectuer une itération.  
  
 `statements`  
 Facultatif. Une ou plusieurs instructions à exécuter pour chaque propriété de `object` ou chaque élément de `array`. Il peut s'agir d'une instruction composée.  
  
## <a name="remarks"></a>Remarques  
 Au début de chaque itération d’une boucle, la valeur de `variable` est le nom de propriété suivant `object` ou l’index de l’élément suivant de `array`. Vous pouvez ensuite utiliser `variable` dans les instructions à l’intérieur de la boucle pour référencer la propriété de `object` ou l’élément de `array`.  
  
 Les propriétés d’un objet ne sont pas affectées de manière déterminée. Vous ne pouvez pas spécifier une propriété spécifique par son index, uniquement par le nom de la propriété.  
  
 Effectuer une itération au sein d’un tableau est effectuée dans l’ordre des éléments, c'est-à-dire 0, 1, 2.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de la `for...in` instruction avec un objet utilisé comme tableau associatif.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre l’utilisation de la `for ... in` instruction pour parcourir un `Array` objet qui a des propriétés expando.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Utilisez le `Enumerator` objet pour itérer sur les membres d’une collection.  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction for](../../javascript/reference/for-statement-javascript.md)   
 [Instruction while](../../javascript/reference/while-statement-javascript.md)