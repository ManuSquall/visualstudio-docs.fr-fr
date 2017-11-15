---
title: "Itérateurs et générateurs (JavaScript) | Microsoft Docs"
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
ms.assetid: 68ef5b2f-0349-492b-b557-73ff2a2f90cf
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c27969609a38b87b15c727e9c8aef89ee77032
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iterators-and-generators-javascript"></a>Itérateurs et générateurs (JavaScript)
Un itérateur est un objet qui sert à parcourir un objet conteneur telle qu'une liste. En JavaScript, un objet itérateur n'est pas un objet intégré distinct, mais un objet qui implémente une méthode `next` pour accéder à l'élément suivant dans l'objet conteneur.  
  
 Dans [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], vous pouvez créer vos propres itérateurs personnalisés. Toutefois, il est généralement plus facile d'utiliser des générateurs, qui simplifient considérablement la création des itérateurs. Les générateurs sont un type de fonction qui est une fabrique pour des itérateurs. Pour créer un itérateur personnalisé à l’aide d’une fonction de générateur, consultez [Générateurs](#Generators).  
  
> [!CAUTION]
>  Les générateurs sont pris en charge dans [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="iterators"></a>Itérateurs  
 L'implémentation d'un itérateur JavaScript implique deux ou trois objets conformes à des interfaces spécifiques :  
  
-   Interface Iterable  
  
-   Interface Iterator  
  
-   Interface IteratorResult  
  
 À l'aide de ces interfaces, vous pouvez créer des itérateurs personnalisés. Cela vous permet de parcourir un objet itérable à l'aide de l'instruction `for…of`.  
  
### <a name="iterable-interface"></a>Interface Iterable  
 L'interface Iterable est l'interface requise pour un objet itérable (objet pour lequel un itérateur peut être obtenu). Par exemple, `C` dans `for (let e of C)` doit implémenter l'interface Iterable.  
  
 Un objet itérable doit fournir la méthode Symbol.iterator, qui retourne un itérateur.  
  
```JavaScript  
obj[Symbol.iterator] = function() { return iterObj; }  
```  
  
 Cette propriété doit être une fonction qui n'accepte aucun argument et retourne un objet (`iterObject`) conforme à l'interface `Iterator`.  
  
 De nombreux types intégrés, y compris les tableaux, sont désormais itérables. La boucle `for…of` consomme un objet itérable. (Toutefois, les itérables intégrés ne sont pas tous des itérateurs. Par exemple, un objet Array n'est pas lui-même un itérateur, mais il est itérable, tandis qu'un ArrayIterator est également itérable.)  
  
### <a name="iterator-interface"></a>Interface Iterator  
 L'objet retourné par la méthode Symbol.iterator doit implémenter la méthode `next`. La méthode `next` a la syntaxe suivante :  
  
```JavaScript  
iterObj.next() = function() { return iterResultObj; };  
```  
  
 La méthode `next` est une fonction qui retourne une valeur. La fonction retourne un objet (`iterResultObj`) conforme à l'interface `IteratorResult`. Si un appel précédent à la méthode `next` d'un itérateur a retourné un objet `IteratorResult` dont la propriété `done` est true, l'itération est interrompue et la méthode `next` n'est plus appelée.  
  
 Les itérateurs peuvent également inclure une méthode `return` pour s'assurer que l'itérateur est supprimé correctement quand le script en a terminé avec lui.  
  
### <a name="iteratorresult-interface"></a>Interface IteratorResult  
 L'interface IteratorResult est l'interface requise pour le résultat de la méthode `next` sur un itérateur. L'objet retourné par `next` doit fournir des propriétés `done` et `value`.  
  
```JavaScript  
var iterResultObj = { done: true|false, value: value }  
```  
  
 La propriété `done` retourne l'état de l'appel de méthode `next` d'un itérateur, true ou false. Si la fin de l'itérateur a été atteinte, `done` retourne la valeur true. Si la fin n'est pas atteinte, `done` retourne false et une valeur est disponible. Si la propriété `done` (soit la sienne, soit une propriété héritée) n'existe pas, le résultat de `done` est considéré comme false.  
  
 Si `done` est false, la propriété `value` retourne la valeur d'élément d'itération actuelle. Si `done` est true, il s'agit de la valeur de retour de l'itérateur, si une valeur de retour est fournie. Si l'itérateur n'a pas de valeur de retour, `value` est non définie. Dans ce cas, la propriété `value` peut être absente de l'objet conforme s'il n'hérite pas d'une propriété de valeur explicite.  
  
<a name="Generators"></a>   
## <a name="generators"></a>Générateurs  
 Pour créer et utiliser facilement des itérateurs personnalisés, créez une fonction de générateur à l'aide de la syntaxe function* avec une ou plusieurs expressions `yield`. La fonction de générateur retourne un itérateur (autrement dit, un générateur), qui permet au corps de la fonction de générateur de s'exécuter. La fonction s'exécute jusqu'à l'instruction `yield` ou `return` suivante.  
  
 Appelez la méthode `next` de l'itérateur pour retourner la valeur suivante à partir de la fonction de générateur.  
  
 L'exemple suivant montre un générateur qui retourne un itérateur pour un objet string.  
  
```JavaScript  
function* stringIter() {  
    var str = "bobsyouruncle";  
    var idx = 0;  
    while(idx < str.length)  
        yield str[idx++];  
}  
  
var si = stringIter();  
  
console.log(si.next().value);  
console.log(si.next().value);  
console.log(si.next().value);  
  
// Output:  
// b  
// o  
// b  
  
```  
  
 Dans un générateur, l'expression d'opérande yield met fin à l'appel à `next` et retourne un objet `IteratorResult` avec deux propriétés, `done` (`done=false`) et `value` (`value=operand`). `operand` est facultatif. Si sa valeur est absente, elle est non définie.  
  
 Dans un générateur, une instruction `return` met fin au générateur en retournant un `IteratorResult` avec `done=true`, ainsi que le résultat de l'opérande facultatif pour la propriété de valeur.  
  
 Vous pouvez également utiliser une expression `yield*` à la place de `yield` pour déléguer à un autre générateur ou à un autre objet itérable, par exemple un tableau ou une chaîne.  
  
 Si vous ajoutez le code suivant à l'exemple précédent, `yield*` délègue au générateur `stringIter`.  
  
```JavaScript  
function* strIter() {  
    yield "jo";  
    yield* stringIter();  
}  
  
var si2 = strIter();  
  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
console.log(si2.next().value);  
  
// Output:  
// jo  
// b  
// o  
// b  
```  
  
 Vous pouvez aussi créer des générateurs plus sophistiqués en passant un argument à `next` et en utilisant cet argument pour modifier l'état du générateur. `next` devient la valeur de résultat de l'expression `yield` exécutée précédemment. Dans l'exemple suivant, quand vous passez une valeur de 100 à la méthode `next`, vous réinitialisez la valeur d'index interne du générateur.  
  
```  
function* strIter() {  
    var str = "jobob";  
    var idx = 0;  
    while(idx , str.length) {  
        var modify = yield str[idx++];  
        if(modify == 100) {  
            idx = 0;  
        }  
    }
}
  
var si3 = strIter();  
  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next().value);  
console.log(si3.next(100).value);  
  
// Output:  
// j  
// o  
// b  
// j  
  
```  
  
 D'autres générateurs avancés peuvent appeler la méthode `throw` du générateur. L'erreur semble être levée au point où le générateur est suspendu (avant l'instruction `yield` suivante).
