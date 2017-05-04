---
title: "Utilisation de constructeurs pour la d&#233;finition de types | Microsoft Docs"
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
  - "constructeurs, créer"
  - "créer des objets, fonctions constructeur"
  - "fonctions, fonctions constructeur"
  - "objets, création (JavaScript)"
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Utilisation de constructeurs pour la d&#233;finition de types
Un constructeur est une fonction qui instancie un type particulier d'[objet](../../javascript/objects-and-arrays-javascript.md).  Vous appelez un constructeur avec le mot clé **new**.  Voici quelques exemples de constructeurs avec des objets JavaScript intégrés et des objets personnalisés.  
  
## Exemples de constructeurs  
  
```javascript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 La fonction constructeur contient le mot clé **this**, qui est une référence à un objet vide venant d'être créé.  Elle initialise le nouvel objet en créant des propriétés et en leur attribuant des valeurs initiales.  Le constructeur retourne une référence à l'objet construit.  
  
## Écrire des constructeurs  
 Vous pouvez créer des objets à l'aide de l'opérateur **new** et de fonctions constructeurs prédéfinies telles que **Object\(\)**, **Date\(\)** et **Function\(\)**.  Vous pouvez également créer des fonctions constructeurs personnalisées qui définissent un ensemble de propriétés et de méthodes.  Voici un exemple de constructeur personnalisé :  
  
```javascript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Lorsque vous appelez le constructeur Circle, vous fournissez des valeurs pour le point central et le rayon du cercle.  Vous obtenez alors un objet Circle qui contient trois propriétés.  Voici comment instancier un objet Circle.  
  
```javascript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 Le type de tous les objets créés avec un constructeur personnalisé est `object`.  Il n'existe que six types dans JavaScript : `object`, `function`, `string`, `number`, `boolean` et `undefined`.  Pour plus d'informations, consultez [typeof, opérateur](../../javascript/reference/typeof-operator-decrementjavascript.md).  
  
## Voir aussi  
 [Utilisation de la méthode Bind](../../javascript/advanced/using-the-bind-method-javascript.md)