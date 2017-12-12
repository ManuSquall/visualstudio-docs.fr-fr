---
title: "Portée des variables (JavaScript) | Microsoft Docs"
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
- scope, JavaScript
- variable scope [JavaScript]
- variables, scope [JavaScript]
ms.assetid: a811a9a6-856f-46e9-8be3-f2d22a0c245f
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5afc99bf3d1006b68e1d6c4c8d5bbcfc90eb776f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="variable-scope-javascript"></a>Portée des variables (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] a deux types de portées : globale et locale. Si vous déclarez une variable en dehors d'une définition de fonction, il s'agit d'une variable globale et sa valeur est accessible et modifiable dans tout le programme. En revanche, si vous déclarez une variable au sein d'une définition de fonction, il s'agit d'une variable locale. Elle est créée et détruite chaque fois que la fonction est exécutée ; en dehors de cette fonction, aucun code ne peut y accéder. JavaScript ne prend pas en charge la portée de bloc (un ensemble d’accolades `{. . .}` définissant une nouvelle portée), sauf dans le cas particulier de variables ayant une portée de bloc.  
  
## <a name="scope-in-javascript"></a>Portée dans JavaScript  
 Une variable locale peut posséder le même nom qu'une variable globale, mais elle est entièrement dissociée de celle-ci. La modification de la valeur d'une variable n'a aucun effet sur l'autre variable. Seule la version locale est significative au sein de la fonction dans laquelle elle est déclarée.  
  
```JavaScript  
// Global definition of aCentaur.  
var aCentaur = "a horse with rider,";  
  
// A local aCentaur variable is declared in this function.  
function antiquities(){  
  
   var aCentaur = "A centaur is probably a mounted Scythian warrior";  
}  
  
antiquities();  
aCentaur += " as seen from a distance by a naive innocent.";  
  
document.write(aCentaur);  
  
// Output: "a horse with rider, as seen from a distance by a naive innocent."  
```  
  
 Dans JavaScript, les variables sont évaluées comme si elles étaient déclarées au début de la portée dans laquelle elles existent. Cela provoque parfois des résultats inattendus, comme illustré ici.  
  
```JavaScript  
var aNumber = 100;  
tweak();  
  
function tweak(){  
  
    // This prints "undefined", because aNumber is also defined locally below.  
    document.write(aNumber);  
  
    if (false)  
    {  
        var aNumber = 123;    
    }  
}  
```  
  
 Lorsque [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute une fonction, il recherche d'abord toutes les déclarations de variable, par exemple `var someVariable;`. Il crée les variables avec la valeur initiale `undefined`. Si une variable est déclarée avec une valeur, par exemple `var someVariable = "something";`, sa valeur initiale reste `undefined`. Elle adopte la valeur déclarée uniquement à partir du moment où la ligne contenant la déclaration est exécutée.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] traite toutes les déclarations de variables avant d'exécuter du code, que la déclaration se trouve ou non à l'intérieur d'un bloc conditionnel ou de toute autre construction. Après avoir trouvé toutes les variables, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] exécute le code dans la fonction. Si une variable est implicitement déclarée à l'intérieur d'une fonction, autrement dit, si elle apparaît à gauche d'une expression d'assignation mais qu'elle est déclarée sans le mot clé `var`, elle est créée en tant que variable globale.  
  
 Dans JavaScript, une fonction (imbriquée) interne enregistre les références aux variables locales présentes dans la même portée que la fonction elle-même, même si la fonction retourne. Cet ensemble de références est appelé fermeture. Dans l'exemple suivant, le deuxième appel à la fonction interne affiche le même message (« Hello Bill ») que le premier appel, car le paramètre d'entrée pour la fonction externe, `name`, est une variable locale stockée dans la fermeture de la fonction interne.  
  
```JavaScript  
function send(name) {  
    // Local variable 'name' is stored in the closure  
    // for the inner function.  
    return function () {  
        sendHi(name);  
    }  
}  
  
function sendHi(msg) {  
    console.log('Hello ' + msg);  
}  
  
var func = send('Bill');  
func();  
// Output:  
// Hello Bill  
sendHi('Pete');  
// Output:  
// Hello Pete  
func();  
// Output:  
// Hello Bill  
```  
  
## <a name="block-scoped-variables"></a>Variables de portée de bloc  
 Internet Explorer 11 propose la prise en charge de [let](../../javascript/reference/let-statement-javascript.md) et de [const](../../javascript/reference/const-statement-javascript.md), qui sont des variables de portée de bloc. Pour ces variables, les accolades `{. . .}` définissent une nouvelle portée. Lorsque vous affectez l'une de ces variables à une valeur particulière, la valeur s'applique uniquement à la portée dans laquelle elle est définie.  
  
 L'exemple suivant illustre l'utilisation de `let` et de la portée de bloc.  
  
> [!NOTE]
>  Le code suivant est pris en charge dans les mode standard d'Internet Explorer 11 et versions ultérieures.  
  
```JavaScript  
let x = 10;  
var y = 10;  
{  
    let x = 5;  
    var y = 5;  
    {  
        let x = 2;  
        var y = 2;  
        document.write("x: " + x + "<br/>");  
        document.write("y: " + y + "<br/>");  
        // Output:  
        // x: 2  
        // y: 2  
    }  
    document.write("x: " + x + "<br/>");  
    document.write("y: " + y + "<br/>");  
    // Output:  
    // x: 5  
    // y: 2  
}  
  
document.write("x: " + x + "<br/>");  
document.write("y: " + y + "<br/>");  
// Output:  
// x: 10  
// y: 2  
```