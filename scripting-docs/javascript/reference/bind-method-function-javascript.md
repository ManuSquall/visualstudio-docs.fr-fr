---
title: "bind, m&#233;thode (Function) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "arguments (JavaScript), bind (méthode)"
  - "bind (méthode) (JavaScript)"
  - "paramètres (JavaScript), bind (méthode)"
  - "this (mot clé) (JavaScript), bind (méthode)"
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# bind, m&#233;thode (Function) (JavaScript)
Pour une fonction donnée, crée une fonction liée qui a le même corps que la fonction d'origine.  Dans la fonction liée, l'objet `this` résout l'objet passé.  La fonction liée a les paramètres initiaux spécifiés.  
  
## Syntaxe  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### Paramètres  
 `function`  
 Obligatoire.  Objet de fonction.  
  
 `thisArg`  
 Obligatoire.  Objet auquel le mot clé `this` peut faire référence dans la nouvelle fonction.  
  
 `arg1`\[,`arg2`\[,`argN`\]\]\]  
 Facultatif.  Liste des arguments à passer à la nouvelle fonction.  
  
## Valeur de retour  
 Nouvelle fonction qui est identique à la fonction `function`, à l'exception de l'objet `thisArg` et des arguments initiaux.  
  
## Exceptions  
 Si le paramètre `function` spécifié n'est pas une fonction, une exception `TypeError` est levée.  
  
## Exemple  
 Le code suivant met en œuvre la méthode `bind`.  
  
```javascript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## Exemple  
 Dans l'exemple suivant, l'objet `thisArg` est différent de l'objet qui contient la méthode d'origine.  
  
```javascript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## Exemple  
 Le code suivant illustre l'utilisation des arguments `arg1[,arg2[,argN]]]`.  La fonction liée utilise les paramètres spécifiés dans la méthode `bind` comme premier et deuxième paramètres.  Tous les paramètres spécifiés lorsque la fonction liée est appelée sont utilisés en tant que troisième paramètre, quatrième paramètre, et ainsi de suite.  
  
```javascript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## Configuration requise  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)   
 [filter, méthode \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Utilisation de la méthode Bind](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Exemple d'application Hilo JavaScript \(Windows Store\)](http://hilojs.codeplex.com/SourceControl/latest)