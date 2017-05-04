---
title: "Prototypes et h&#233;ritage de prototypes | Microsoft Docs"
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
  - "prototype (JavaScript)"
  - "héritage de prototypes (JavaScript)"
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Prototypes et h&#233;ritage de prototypes
En JavaScript, `prototype` est une propriété des fonctions, ainsi que des objets créés par les fonctions constructeurs.  Le prototype d'une fonction est un objet.  Il est principalement employé lorsqu'une fonction est utilisée en tant que constructeur.  
  
```javascript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 Dans l'exemple ci\-dessus, le prototype de la fonction `Vehicle` est le prototype de tout objet instancié avec le constructeur `Vehicle`.  
  
## Utilisation de prototypes pour ajouter des propriétés et des méthodes  
 Vous pouvez utiliser la propriété `prototype` pour ajouter des propriétés et des méthodes aux objets, même ceux qui ont déjà été créés :  
  
```javascript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 La valeur de `testColor` est « red ».  
  
 Vous pouvez également ajouter des propriétés et des méthodes aux objets prédéfinis.  Par exemple, vous pouvez définir une méthode `Trim` sur l'objet prototype `String` pour que toutes les chaînes de votre script héritent de la méthode.  
  
```javascript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### Utilisation de prototypes pour dériver un objet d'un autre objet à l'aide d'Object.create  
 L'objet `prototype` peut être utilisé pour dériver un objet d'un autre.  Par exemple, vous pouvez utiliser la fonction [Object.create](../../javascript/reference/object-create-function-javascript.md) pour dériver un nouvel objet `Bicycle` à l'aide du prototype de l'objet `Vehicle` défini précédemment \(et lui ajouter les nouvelles propriétés dont vous avez éventuellement besoin\).  
  
```javascript  
var Bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 L'objet `Bicycle` contient les propriétés `wheels`, `engine`, `color` et `pedals`, et son prototype est `Vehicle.prototype`.  Le moteur JavaScript recherche la propriété `pedals` sur `Bicycle`, puis effectue une recherche sur la chaîne de prototype pour trouver les propriétés `wheels`, `engine` et `color` de `Vehicle`.  
  
### Modification du prototype d'un objet  
 Dans Internet Explorer 11, vous pouvez remplacer le prototype interne d'un objet ou d'une fonction par un nouveau prototype en utilisant la propriété [\_\_proto](../../javascript/reference/proto-property-object-javascript.md).  Lorsque vous utilisez cette propriété, vous héritez les propriétés et les méthodes du nouveau prototype, ainsi que les autres propriétés et méthodes de sa chaîne prototype.  
  
 L'exemple suivant montre comment modifier le prototype d'un objet.  Cet exemple indique comment les propriétés héritées de l'objet changent lorsque vous modifiez son prototype.  
  
```javascript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```