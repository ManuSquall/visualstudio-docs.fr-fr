---
title: "WeakMap, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WeakMap, objet (JavaScript)
Collection de paires clé\/valeur dans lesquelles chaque clé est une référence d'objet.  
  
## Syntaxe  
  
```  
weakmapObj = new WeakMap()  
```  
  
## Notes  
 Un objet `WeakMap` ne peut pas être énuméré.  
  
 Si vous ajoutez une valeur à la collection à l'aide d'une clé existante, la nouvelle valeur remplace l'ancienne valeur.  
  
 Dans un objet `WeakMap`, les références aux objets clés sont conservées « faiblement ».  Cela signifie que `WeakMap` n'empêche pas qu'un garbage collection ne se produise sur les principaux objets.  Lorsqu'il n'y a aucune référence \(autre que `WeakMap`\) aux objets principaux, le garbage collector peut collecter les principaux objets.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `WeakMap`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Constructeur](../../javascript/reference/constructor-property-weakmap.md)|Spécifie la fonction qui crée un `WeakMap`.|  
|[prototype](../../javascript/reference/prototype-property-weakmap.md)|Retourne une référence au prototype d'un `WeakMap`.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `WeakMap`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Supprime tous les éléments d'une `WeakMap`.|  
|[supprimer](../../javascript/reference/delete-method-weakmap-javascript.md)|Supprime un élément spécifié dans un `WeakMap`.|  
|[Obtenir](../../javascript/reference/get-method-weakmap-javascript.md)|Retourne un élément spécifié d'un `WeakMap`.|  
|[a](../../javascript/reference/has-method-weakmap-javascript.md)|Retourne `true` si le `WeakMap` contient un élément spécifié.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Ajoute un nouvel élément à un `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Retourne une représentation sous forme de chaîne d'un `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à un objet `WeakMap`, puis les récupérer.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]