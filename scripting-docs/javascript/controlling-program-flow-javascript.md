---
title: Contrôle du flux de programme (JavaScript) | Microsoft Docs
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
- Boolean values, program flow
- continue statement
- break statement
- control flow, about control flow
ms.assetid: 4ef58c82-e5d6-4b09-9458-cf0aa3b39bf5
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20c256d26c6991067d7c25c0c835eda6e5e5aac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569709"
---
# <a name="controlling-program-flow-javascript"></a>Contrôle du flux de programme (JavaScript)
Normalement, les instructions d'un script [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sont exécutées l'une après l'autre, selon l'ordre dans lequel elles sont écrites. C'est pourquoi on parle d'exécution séquentielle. C'est la direction par défaut du déroulement du programme.  
  
 Une alternative à l'exécution séquentielle consiste à transférer le flux du programme vers une autre partie de votre script. Par conséquent, au lieu de l'instruction suivante de la séquence, une autre instruction est exécutée à la place.  
  
 Pour que le script présente une utilité, ce transfert de contrôle doit être effectué de manière logique. Le transfert du contrôle du programme est basé sur une décision, dont le résultat est une instruction booléenne (qui retourne une valeur **true** ou **false**). Vous créez une expression, puis vérifiez si son résultat donne la valeur true. Il existe deux types principaux de structures de programme pour y parvenir.  
  
 La première est la structure de sélection. Vous pouvez l'utiliser pour spécifier des alternatives au flux du programme, en créant une jonction dans votre programme (comme un embranchement sur une route). Quatre structures de sélection sont disponibles dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] :  
  
-   La structure de sélection simple (**if**)  
  
-   La structure de sélection double (**if/else**)  
  
-   L'opérateur ternaire inline `?:`  
  
-   La structure de sélection multiple (`switch`)  
  
 Le deuxième type de structure de contrôle du programme est la structure à répétition. Vous pouvez l'utiliser pour spécifier qu'une action doit être répétée tant qu'une condition demeure vraie (true). Lorsque les conditions de l'instruction de contrôle sont remplies (généralement après un certain nombre d'itérations), le contrôle passe à l'instruction qui suit la structure à répétition. Quatre structures à répétition sont disponibles dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] :  
  
-   L'expression est testée en début de boucle (`while`)  
  
-   L’expression est testée en fin de boucle (**do/while**)  
  
-   L’expression fonctionne sur chacune des propriétés d’un objet (**for/in**)  
  
-   La répétition est contrôlée par un compteur (**for**)  
  
 Vous pouvez créer des scripts très complexes en imbriquant et en empilant les structures de contrôle de sélection et de répétition.  
  
 La gestion des exceptions, qui n'est pas abordée dans ce document, constitue une troisième forme de flux de programme structurée.  
  
## <a name="using-conditional-statements"></a>Utilisation d'instructions conditionnelles  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prend en charge les instructions conditionnelles **if** et [if...else](../javascript/reference/if-dot-dot-dot-else-statement-javascript.md). Dans les instructions **if**, une condition est testée, et si la condition passe le test, le code [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] approprié est exécuté. Dans l'instruction `if...else`, un code différent est exécuté si la condition échoue au test. Dans sa forme la plus simple, une instruction **if** peut tenir sur une ligne, mais les instructions **if** et `if...else` multilignes sont beaucoup plus habituelles.  
  
 Dans les exemples suivants, vous trouverez des syntaxes que vous pouvez utiliser avec les instructions **if** et `if...else`. Le premier exemple est un test booléen dans sa forme la plus simple. L’instruction ou le bloc d’instructions qui suit **if** est exécuté si (et seulement si) l’élément entre parenthèses prend la valeur (ou peut être contraint à prendre la valeur) **true**.  
  
```JavaScript  
function GetReaction(newShip, color, texture, dayOfWeek)  
{  
   // The test succeeds if the newShip Boolean value is true.  
   if (newShip)  
   {  
      return "Champagne Bottle";  
   }  
  
   // The test succeeds if both conditions are true.  
   if (color == "deep yellow" && texture == "large and small wrinkles")  
   {  
      return "Is it a crenshaw melon?";  
   }  
  
   // The test succeeds if either condition is true.  
   if ((dayOfWeek == "Saturday") || (dayOfWeek == "Sunday"))  
   {  
      return "I'm off to the beach!";  
   }  
   else  
   {  
      return "I'm going to work.";  
   }  
}  
  
var reaction = GetReaction(false, "deep yellow", "smooth", "Sunday");  
document.write(reaction);  
  
// Output: I'm off to the beach!  
```  
  
## <a name="conditional-operator"></a>Opérateur conditionnel  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prend également en charge une forme conditionnelle implicite. Il utilise un point d’interrogation après la condition à tester (plutôt que le mot **if** avant la condition). Propose également deux alternatives, l'une à utiliser si la condition est remplie et l'autre si elle ne l'est pas. Un signe deux-points doit séparer ces alternatives.  
  
```JavaScript  
var AMorPM = (theHour >= 12) ? "PM" : "AM";  
```  
  
 Si vous devez tester simultanément plusieurs conditions dont l'une est plus susceptible de réussir ou d'échouer que les autres, vous pouvez faire appel à une fonctionnalité appelée « évaluation par court-circuit » pour accélérer l'exécution de votre script. Lorsque [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] évalue une expression logique, il se contente d'évaluer le nombre de sous-expressions requises pour obtenir un résultat.  
  
 Par exemple, pour une expression AND de type ((x == 123) && (y == 6)), [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contrôle d'abord si x est égal à 123. Dans le cas contraire, l'expression globale ne peut pas avoir la valeur true, même si y est égal à 6. Ainsi, le test d’y n’est jamais effectué et [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] retourne la valeur **false**.  
  
 De même, si une seule condition parmi plusieurs doit avoir la valeur **true** (à l’aide de l’opérateur &#124;&#124;), le test s’arrête dès qu’une condition réussit le test. Ceci est valable lorsque les conditions à tester impliquent l'exécution d'appels de fonction ou d'autres expressions complexes. Ainsi, quand vous créez ou écrivez des expressions OR, pensez à placer en premier les conditions les plus susceptibles de prendre la valeur **true**. Quand vous écrivez des expressions AND, placez en premier les conditions les plus susceptibles de prendre la valeur **false**.  
  
 L’un des avantages offerts par ce type de conception de script tient au fait que **runsecond()** n’est pas exécuté dans l’exemple suivant si **runfirst()** retourne 0.  
  
```JavaScript  
if ((runfirst() == 0) || (runsecond() == 0)) {  
    // some code  
}  
```  
  
## <a name="using-loops"></a>Utilisation de boucles  
 Il existe plusieurs moyens d'exécuter une instruction ou un bloc d'instructions de façon répétée. En général, l’exécution répétitive est appelée *bouclage* ou *itération*. Une itération consiste simplement à exécuter une seule fois une boucle. Elle est normalement contrôlée par le test d'une variable, dont la valeur change chaque fois que la boucle est exécutée. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prend en charge quatre types de boucles : [for](../javascript/reference/for-statement-javascript.md), [for...in](../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), [while](../javascript/reference/while-statement-javascript.md) et [do...while](../javascript/reference/do-dot-dot-dot-while-statement-javascript.md).  
  
## <a name="using-for-loops"></a>Utilisation de boucles for  
 L’instruction **for** spécifie une variable compteur, une condition de test et une action qui met à jour le compteur. Immédiatement avant chaque itération de la boucle, la condition est testée. Si le test est positif, le code à l'intérieur de la boucle est exécuté. Dans le cas contraire, ce code n'est pas exécuté et le programme continue à partir de la première ligne de code qui suit immédiatement la boucle. Après l'exécution de la boucle, la variable compteur est mise à jour avant l'itération suivante.  
  
 Si la condition n'est jamais remplie, la boucle ne s'exécute jamais. En revanche, si la condition est toujours vérifiée, il se crée une boucle sans fin. Si le premier cas peut s'avérer parfois utile, les boucles sans fin sont presque toujours problématiques. Soyez donc prudent lorsque vous écrivez vos conditions de boucle.  
  
```JavaScript  
// The update expression ("icount++" in the following examples)  
// is executed at the end of the loop, after the block of  
// statements that forms the body of the loop is executed, and  
// before the condition is tested.  
  
// Set a limit of 10 on the loop.  
var howFar = 10;  
  
// Create an array called sum with 10 members, 0 through 9.  
var sum = new Array(howFar);  
sum[0] = 0;  
  
// Iterate from 0 through 9.  
var theSum = 0;  
for(var icount = 0; icount < howFar; icount++)  
{  
   theSum += icount;  
   sum[icount] = theSum;  
}  
  
// This code is not executed at all, because icount is not greater than howFar.  
var newSum = 0;  
for(var icount = 0; icount > howFar; icount++)  
{  
   newSum += icount;  
}  
  
// This is an infinite loop.  
var sum = 0;  
for(var icount = 0; icount >= 0; icount++)  
{  
   sum += icount;  
}  
```  
  
## <a name="using-forin-loops"></a>Utilisation de boucles for...in  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] fournit un type de boucle spécial permettant de parcourir toutes les propriétés définies par l’utilisateur d’un [objet](../javascript/objects-and-arrays-javascript.md), ou tous les éléments d’un tableau. Le compteur de boucle d'une boucle `for...in` est une chaîne, et non un nombre. Contient le nom de la propriété actuelle ou l'index de l'élément de tableau en cours.  
  
```JavaScript  
// Create an object with some properties  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 1234";  
  
// Enumerate (loop through)_all the properties in the object  
for (var prop in myObject)  
{  
    // This displays "The property 'name' is James", etc.  
    document.write("The property '" + prop + "' is " + myObject[prop]);  
    // New line.  
    document.write("<br />");    
}  
```  
  
 Bien que les boucles `for...in` semblent identiques aux boucles VBScript `For Each...Next`, elles ne fonctionnent pas de la même façon. La boucle [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**for...in** itère au sein des propriétés des objets [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. La boucle VBScript **For Each...Next** itère au sein des éléments d’une collection. Pour parcourir en boucle des collections dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], vous devez utiliser l’objet [Énumérateur](../javascript/reference/enumerator-object-javascript.md) ou, si elle est présente, la méthode `forEach` de l’objet collection. Bien que certains objets, tels que ceux contenus dans Internet Explorer, prennent en charge la boucle VBScript **For Each...Next** et la boucle [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]**for...in**, ce n’est pas le cas de la plupart des objets.  
  
## <a name="using-while-loops"></a>Utilisation de boucles while  
 Une boucle `while` est similaire à une boucle **for**. Ces deux boucles se distinguent en ceci qu'une boucle `while` n'a pas de variable compteur ou d'expression de mise à jour intégrée. Pour contrôler l'exécution répétitive d'une instruction ou d'un bloc d'instructions avec une règle plus complexe que celle qui consiste simplement à exécuter n fois le code, utilisez une boucle `while`. L'exemple suivant utilise le modèle objet Internet Explorer et une boucle `while` pour poser une question simple à l'utilisateur.  
  
```JavaScript  
var x = 0;  
while ((x != 5) && (x != null))  
{  
    x = window.prompt("What is my favorite number?", x);  
}  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
> [!NOTE]
>  Les boucles `while` ne disposant pas de variables compteur intégrées explicites, elles sont encore plus vulnérables que les autres aux boucles sans fin. En outre, dans la mesure où il n'est pas toujours facile de découvrir où et quand une condition de boucle est mise à jour, il existe un risque réel d'écrire une boucle `while` dans laquelle la condition n'est en fait jamais mise à jour. Pour cette raison, soyez particulièrement prudents lors de la création de boucles `while`.  
  
 Comme mentionné ci-dessus, il existe également une boucle **do...while** dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] semblable à la boucle while, à ceci près que son exécution est garantie au moins une fois, étant donné que la condition est testée en fin de boucle et non au début. Par exemple, la boucle au-dessus peut être réécrite comme suit :  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
} while ((x != 5) && (x != null));  
  
if (x == null)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```  
  
## <a name="using-break-and-continue-statements"></a>Utilisation d'instructions break et continue  
 Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], l’instruction [break](../javascript/reference/break-statement-javascript.md) permet d’arrêter l’exécution d’une boucle si une condition est remplie. (Notez que l’instruction **break** est également utilisée pour quitter un bloc `switch`.) Vous pouvez utiliser l’instruction [continue](../javascript/reference/continue-statement-javascript.md)pour passer immédiatement à l’itération suivante, tout en sautant le reste du bloc de code et en mettant à jour la variable compteur s’il s’agit d’une boucle **for** ou `for...in`.  
  
 L’exemple suivant repose sur l’exemple précédent et utilise les instructions **break** et **continue** pour contrôler la boucle.  
  
```JavaScript  
var x = 0;  
do  
{  
    x = window.prompt("What is my favorite number?", x);  
  
    // Did the user cancel? If so, break out of the loop  
    if (x == null)  
        break;  
  
    // Did they enter a number?  
    // If so, no need to ask them to enter a number.  
    if (Number(x) == x)  
        continue;  
  
    // Ask user to only enter in numbers  
    window.alert("Please only enter in numbers!");  
  
} while (x != 5)  
  
if (x != 5)  
    window.alert("You gave up!");  
else  
    window.alert("Correct answer!");  
```