---
title: "Cr&#233;ation d&#39;objets (JavaScript) | Microsoft Docs"
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
  - "fonctions constructeur"
  - "constructeurs, inclure les propriétés et les méthodes"
  - "créer des objets"
  - "créer des objets, à propos de la création d'objets"
  - "créer des objets, fonctions constructeur"
  - "créer des objets, prototypes"
  - "objets personnalisés"
  - "objets personnalisés, créer"
  - "constructeur Function"
  - "initialiser des objets, utilisation de constructeurs"
  - "objets, création (JavaScript)"
  - "objets prototypes"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Cr&#233;ation d&#39;objets (JavaScript)
En JavaScript, vous pouvez créer vos propres objets de différentes manières.  Vous pouvez instancier directement un [Object, objet](../javascript/reference/object-object-javascript.md), puis ajouter vos propres propriétés et méthodes.  Vous pouvez également utiliser la notation de littéral d'objet pour définir votre objet.  Vous pouvez également utiliser une fonction constructeur pour définir un objet.  Pour plus d'informations sur l'utilisation des fonctions constructeurs, consultez [Utilisation de constructeurs pour la définition de types](../javascript/advanced/using-constructors-to-define-types.md).  
  
## Exemple  
 Le code suivant montre comment instancier un objet et ajouter des propriétés.  Dans ce cas, seul l'objet `pasta` possède les propriétés `grain`, `width` et `shape`.  
  
```javascript  
var pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## Littéraux d'objet  
 Vous pouvez également utiliser la notation de littéral d'objet quand vous souhaitez créer une seule instance d'un objet.  Le code suivant montre comment instancier un objet en utilisant la notation littérale d'objet.  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 Vous pouvez également utiliser un littéral d'objet dans un constructeur.  
  
> [!CAUTION]
>  Les fonctionnalités décrites ci\-dessous sont prises en charge uniquement en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 En [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)], vous pouvez utiliser une syntaxe abrégée pour créer un littéral d'objet.  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 L'exemple suivant illustre l'utilisation de la syntaxe abrégée pour définir des méthodes dans les littéraux d'objet.  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 Vous pouvez également définir des noms de propriété dynamiquement dans les littéraux d'objet en [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  L'exemple de code suivant crée un nom de propriété pour un objet dynamiquement à l'aide de la syntaxe set.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 L'exemple de code suivant crée un nom de propriété pour un objet dynamiquement à l'aide de la syntaxe get.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 L'exemple de code suivant crée une propriété calculée à l'aide d'une [syntaxe de fonction Arrow](../javascript/functions-javascript.md) pour ajouter 42 au nom de propriété.  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```