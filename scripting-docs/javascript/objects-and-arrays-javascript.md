---
title: "Objets et tableaux (JavaScript) | Microsoft Docs"
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
  - "tableaux (JavaScript)"
  - "tableaux (JavaScript), objets"
ms.assetid: f5106284-1240-4f47-8c3b-5a45e227e5e1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Objets et tableaux (JavaScript)
Les objets [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sont des collections de propriétés et de méthodes.  Une méthode est une fonction membre d'un objet.  Une propriété est une valeur ou un ensemble de valeurs \(sous la forme d'un tableau ou d'un objet\), membre d'un objet.  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prend en charge quatre types d'objets :  
  
-   Les objets intrinsèques, tels que `Array` et `String`.  
  
-   Les objets que vous créez.  
  
-   Les objets hôtes, tels que `window` et `document`.  
  
-   Les objets ActiveX.  
  
## Propriétés et méthodes Expando  
 Tous les objets en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prennent en charge les propriétés et les méthodes expando, c'est\-à\-dire celles qui peuvent être ajoutées ou supprimées au moment de l'exécution.  Ces propriétés et ces méthodes peuvent avoir n'importe quel nom et peuvent être identifiées par des nombres.  Si le nom de la propriété ou de la méthode est un simple identificateur, il peut être écrit après un nom d'objet avec un point, comme `myObj.name`, `myObj.age` et `myObj.getAge` dans l'exemple suivant :  
  
```javascript  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.age = 42;  
  
myObj.getAge =   
    function () {  
        return this.age;  
    };  
  
document.write(myObj.name);  
document.write("<br/>");  
document.write(myObj.age);  
document.write("<br/>");  
document.write(myObj.getAge());  
  
// Output:  
// Fred  
// 42  
// 42  
  
```  
  
 Si le nom de la propriété ou de la méthode n'est pas un simple identificateur, ou s'il n'est pas connu au moment où vous écrivez le script, utilisez une expression comprise entre crochets pour indexer la propriété.  Les noms des propriétés expando en [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sont tous convertis en chaînes avant d'être ajoutés à l'objet.  
  
```javascript  
var myObj = new Object();  
  
// Add two expando properties that cannot be written in the  
// object.property syntax.  
// The first contains invalid characters (spaces), so must be  
// written inside square brackets.  
myObj["not a valid identifier"] = "This is the property value";  
  
// The second expando name is a number, so it also must  
// be placed inside square brackets  
myObj[100] = "100";  
```  
  
 Pour plus d'informations sur la création d'un objet à partir d'une définition, consultez [Création d'objets](../javascript/creating-objects-javascript.md).  
  
## Tableaux comme objets  
 Dans [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], les objets et les tableaux sont gérés quasiment de la même manière, car les tableaux sont simplement un type particulier d'objet.  Les objets et les tableaux peuvent avoir des propriétés et des méthodes.  
  
 Les tableaux ont une propriété `length`, mais les objets n'en ont pas.  Lorsque vous assignez une valeur à un élément d'un tableau dont l'index est supérieur à sa longueur \(par exemple, `myArray[100] = "hello"`\), la propriété `length` est augmentée automatiquement à la nouvelle longueur.  De même, si la valeur de la propriété `length` est inférieure à sa valeur précédente, tout élément dont l'index est en dehors de la longueur du tableau est supprimé.  
  
```javascript  
// An array with three elements  
var myArray = new Array(3);  
  
// Add some data  
myArray[0] = "Hello";  
myArray[1] = 42;  
myArray[2] = new Date(2000, 1, 1);  
  
document.write("original length is: " + myArray.length);  
document.write("<br/>");  
// Add some expando properties  
myArray.expando = "JavaScript!";  
myArray["another Expando"] = "Windows";  
  
// This will still display 3, since the two expando properties  
// don't affect the length.  
document.write("new length is : " + myArray.length);  
  
// Output:  
// original length is: 3  
// new length is : 3  
  
```  
  
 Les tableaux fournissent des méthodes d'itération et de manipulation des membres.  L'exemple suivant montre comment obtenir les propriétés des objets stockés dans un tableau.  
  
```javascript  
var myArray = new Array(3);  
  
// Add some data  
for(var i = 1; i <= 3; i++) {  
    myArray[i] = new Date(2000 + i, 1, 1);  
}  
  
myArray.forEach(function (item) {  
    document.write(item.getFullYear());  
});  
  
// Output:  
// 2001  
// 2002  
// 2003  
```  
  
## Tableaux multidimensionnels  
 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ne prend pas en charge les tableaux multidimensionnels, mais vous pouvez obtenir leur comportement en enregistrant des tableaux dans les éléments d'un autre tableau. \(Vous pouvez enregistrer tout type de données dans des éléments de tableau, y compris d'autres tableaux.\) Par exemple, le code suivant génère un tableau de multiplication pour les nombres allant jusqu'à 5.  
  
```javascript  
// The size of the table.  
var iMaxNum = 5;  
// Loop counters.  
var i, j;  
  
// Set the length of the array to iMaxNum + 1.   
// The first array index is zero, not 1.  
var MultiplicationTable = new Array(iMaxNum + 1);  
  
// Loop for each major number (each row in the table)  
for (i = 1; i <= iMaxNum; i++)  
{  
    // Create the columns in the table  
    MultiplicationTable[i] = new Array(iMaxNum + 1);  
  
    // Fill the row with the results of the multiplication  
    for (j = 1; j <= iMaxNum; j++)  
    {  
        MultiplicationTable[i][j] = i * j;  
    }  
}  
  
document.write(MultiplicationTable[3][4]);  
document.write("<br/>");   
document.write(MultiplicationTable[5][2]);  
document.write("<br/>");  
document.write(MultiplicationTable[1][4]);  
  
// Output:  
// 12  
// 10  
// 4  
  
```