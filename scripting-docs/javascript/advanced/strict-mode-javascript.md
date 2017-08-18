---
title: Strict, mode (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1038
- VS.WebClient.Help.SCRIPT1050
- VS.WebClient.Help.SCRIPT1042
- VS.WebClient.Help.SCRIPT1041
- VS.WebClient.Help.SCRIPT1046
- VS.WebClient.Help.SCRIPT1045
- VS.WebClient.Help.SCRIPT1037
- VS.WebClient.Help.SCRIPT1039
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strict mode
- use strict
ms.assetid: 0f27022a-f41c-4504-965c-5a2701f342cd
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 77ee7d54dd265026b2bf4c9af52a71cccf9a7675
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="strict-mode-javascript"></a>Strict, mode (JavaScript)
Le mode strict permet d'optimiser la vérification des erreurs dans le code. Lorsque vous utilisez le mode strict, vous ne pouvez pas, par exemple, utiliser les variables déclarées implicitement, assigner une valeur à une propriété en lecture seule ou ajouter une propriété à un objet qui n'est pas extensible. Les restrictions sont répertoriées dans la section [Restrictions applicables au code en mode strict](../../javascript/advanced/strict-mode-javascript.md#rest) plus loin dans cette rubrique. Pour plus d’informations sur le mode strict, consultez [Spécification du langage ECMAScript, 5e édition](http://www.ecma-international.org/publications/standards/Ecma-262.htm).  
  
> [!WARNING]
>  Le mode strict n'est pas pris en charge dans les versions Internet Explorer antérieures à Internet Explorer 10.  
  
## <a name="declaring-strict-mode"></a>Déclaration du mode strict  
 Vous pouvez déclarer le mode strict en ajoutant `"use strict";` au début d'un fichier, d'un programme ou d'une fonction. Ce type de déclaration est appelé *prologue de directives*. La portée d'une déclaration de mode strict dépend de son contexte. S'il est déclaré dans un contexte global (hors de la portée d'une fonction), tout le code du programme est en mode strict. S'il est déclaré dans une fonction, tout le code de la fonction est en mode strict. Par exemple, dans l'exemple suivant, tout le code est en mode strict et la déclaration de la variable en dehors de la fonction génère l'erreur de syntaxe « Variable non définie en mode strict ».  
  
```JavaScript  
"use strict";  
function testFunction(){  
    var testvar = 4;  
    return testvar;  
}  
  
// This causes a syntax error.  
testvar = 5;  
  
```  
  
 Dans l'exemple suivant, seul le code situé dans `testFunction` est en mode strict. La déclaration de la variable en dehors de la fonction n'entraîne pas d'erreur de syntaxe, contrairement à la déclaration dans la fonction.  
  
```JavaScript  
function testFunction(){  
    "use strict";  
    // This causes a syntax error.  
    testvar = 4;  
    return testvar;  
}  
testvar = 5;  
  
```  
  
<a name="rest"></a>   
## <a name="restrictions-on-code-in-strict-mode"></a>Restrictions applicables au code en mode strict  
 Le tableau suivant répertorie les restrictions les plus importantes qui s'appliquent en mode strict.  
  
|||||  
|-|-|-|-|  
|**Élément de langage**|**Restriction**|**Error**|**Exemple**|  
|Variable|Utilisation d'une variable sans la déclarer.|SCRIPT5042 : Variable non définie en mode strict|`testvar = 4;`|  
|Propriété en lecture seule|Écriture dans une propriété en lecture seule.|SCRIPT5045 : L'assignation à des propriétés en lecture seule n'est pas autorisée en mode strict|`var testObj = Object.defineProperties({}, {     prop1: {         value: 10,         writable: false // by default     },     prop2: {         get: function () {         }     } }); testObj.prop1 = 20;  testObj.prop2 = 30;`|  
|Propriété non extensible|Ajout d'une propriété à un objet dont l'attribut `extensible` a la valeur `false`.|SCRIPT5046 : Impossible de créer la propriété pour un objet non extensible|`var testObj = new Object();  Object.preventExtensions(testObj);  testObj.name = "Bob";`|  
|`delete`|Suppression d’une variable, d’une fonction ou d’un argument.<br /><br /> Suppression d'une propriété dont l'attribut `configurable` a la valeur `false`.|SCRIPT1045 : Appel de la fonction delete sur \<expression> non autorisé en mode strict|`var testvar = 15; function testFunc() {}; delete testvar; delete testFunc;  Object.defineProperty(testObj, "testvar", {     value: 10,     configurable: false     }); delete testObj.testvar;`|  
|Duplication d'une propriété|Définition d'une propriété à plusieurs reprises dans un littéral d'objet.|SCRIPT1046 : Définition multiple d'une propriété non autorisée en mode strict|`var testObj = {     prop1: 10,     prop2: 15,     prop1: 20 };`|  
|Duplication d'un nom de paramètre|Utilisation d'un nom de paramètre à plusieurs reprises dans une fonction.|SCRIPT1038 : Présence de doublons de nom de paramètre formel non autorisée en mode strict|`function testFunc(param1, param1) {     return 1; };`|  
|Mots clés réservés futurs|Utilisation d'un mot clé réservé futur en tant que nom de variable ou de fonction.|SCRIPT1050 : L'utilisation d'un mot réservé futur pour un identificateur n'est pas valide. Le nom d'identificateur est réservé en mode strict.|-                      `implements`<br /><br /> -                      `interface`<br /><br /> -                      `package`<br /><br /> -                      `private`<br /><br /> -                      `protected`<br /><br /> -                      `public`<br /><br /> -                      `static`<br /><br /> -                      `yield`|  
|Valeurs octales|Assignation d'une valeur octale à un littéral numérique, ou tentative d'utilisation d'un caractère d'échappement sur une valeur octale.|SCRIPT1039 : Présence de littéraux numériques octaux et de caractères d'échappement non autorisée en mode strict|`var testoctal = 010; var testescape = \010;`|  
|`this`|La valeur `this` n'est pas convertie en objet global lorsqu'elle est `null` ou `undefined`.||`function testFunc() {     return this; } var testvar = testFunc();`<br /><br /> En mode non strict, la valeur `testvar` est l'objet global, mais en mode strict, la valeur est `undefined`.|  
|`eval` en tant qu'identificateur|La chaîne « eval » ne peut pas être utilisée comme identificateur (nom de variable ou de fonction, nom de paramètre, etc.).||`var eval = 10;`|  
|Fonction déclarée dans une instruction ou un bloc|Vous ne pouvez pas déclarer une fonction dans une instruction ou un bloc.|SCRIPT1047 : En mode strict, les déclarations de fonction ne peuvent pas être imbriquées dans une instruction ou un bloc. Elles ne peuvent figurer qu'au niveau supérieur ou directement dans le corps d'une fonction.|`var arr = [1, 2, 3, 4, 5]; var index = null; for (index in arr) {     function myFunc() {}; }`|  
|Variable déclarée dans une fonction `eval`|Si une variable est déclarée dans une fonction `eval`, elle ne peut pas être utilisée en dehors de cette fonction.|SCRIPT1041 : Utilisation non valide de 'eval' en mode strict|`eval("var testvar = 10"); testvar = 15;`<br /><br /> L'évaluation indirecte est possible, mais vous ne pouvez toujours pas utiliser de variable déclarée en dehors de la fonction `eval`.<br /><br /> `var indirectEval = eval; indirectEval("var testvar = 10;"); document.write(testVar);`<br /><br /> Ce code entraîne une erreur SCRIPT5009 : « testVar » n'est pas défini.|  
|`Arguments` en tant qu'identificateur|La chaîne « arguments » ne peut pas être utilisée comme identificateur (nom de variable ou de fonction, nom de paramètre, etc.).|SCRIPT1042 : Utilisation non valide d'« arguments » en mode strict|`var arguments = 10;`|  
|`arguments` dans une fonction|Vous ne pouvez pas modifier les valeurs des membres de l'objet `arguments` local.||`function testArgs(oneArg) {     arguments[0] = 20; }`<br /><br /> En mode non strict, vous pouvez modifier la valeur du paramètre `oneArg` en modifiant la valeur `arguments[0]` afin que la valeur d'`oneArg` et d'`arguments[0]` soit égale à 20. En mode strict, la modification de la valeur `arguments[0]` n'affecte pas la valeur de `oneArg`, car l'objet `arguments` est une simple copie locale.|  
|`arguments.callee`|Non autorisé.||`function (testInt) {     if (testInt-- == 0)         return;     arguments.callee(testInt--); }`|  
|`with`|Non autorisé.|SCRIPT1037 : Les instructions « with » ne sont pas autorisées en mode strict|`with (Math){     x = cos(3);     y = tan(7); }`|
