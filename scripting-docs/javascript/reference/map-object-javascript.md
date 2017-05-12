---
title: "Map, objet (JavaScript) | Microsoft Docs"
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
  - "Map"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Map, objet (JavaScript)
Collection de paires clé\-valeur.  
  
## Syntaxe  
  
```javascript  
mapObj = new Map()  
```  
  
## Notes  
 Les clés et les valeurs de la collection peuvent être de n'importe quel type.  Si vous ajoutez une valeur à la collection à l'aide d'une clé existante, la nouvelle valeur remplace l'ancienne valeur.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Map`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Constructeur](../../javascript/reference/constructor-property-map.md)|Spécifie la fonction qui crée un mappage.|  
|[prototype](../../javascript/reference/prototype-property-map.md)|Retourne une référence au prototype pour un mappage.|  
|[taille](../../javascript/reference/size-property-map-javascript.md)|Retourne le nombre d'éléments d'un mappage.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Map`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|Supprime tous les éléments dans un mappage.|  
|[supprimer](../../javascript/reference/delete-method-map-javascript.md)|Supprime un élément spécifié dans un mappage.|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|Exécute l'action spécifiée pour chaque élément du mappage.|  
|[Obtenir](../../javascript/reference/get-method-map-javascript.md)|Retourne un élément spécifique à partir d'un mappage.|  
|[a](../../javascript/reference/has-method-map-javascript.md)|Retourne `true` si le mappage contient un élément spécifié.|  
|[set](../../javascript/reference/set-method-map-javascript.md)|Ajoute un élément à un mappage.|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|Retourne une représentation d'un mappage sous forme de chaîne.|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à `Map`, puis les récupérer.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]