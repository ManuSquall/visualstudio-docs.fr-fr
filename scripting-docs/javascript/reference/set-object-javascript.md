---
title: "Set, objet (JavaScript) | Microsoft Docs"
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
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Set, objet (JavaScript)
Collection de valeurs uniques qui peuvent être de tout type.  
  
## Syntaxe  
  
```  
setObj = new Set()  
  
```  
  
## Notes  
 Si vous essayez d'ajouter une valeur non unique à `Set`, la nouvelle valeur ne sera pas ajoutée à la collection.  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Set`.  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Constructeur](../../javascript/reference/constructor-property-set.md)|Spécifie la fonction qui crée un ensemble.|  
|[prototype](../../javascript/reference/prototype-property-set.md)|Retourne une référence au prototype pour un ensemble.|  
|[taille](../../javascript/reference/size-property-set-javascript.md)|Retourne le nombre d'éléments d'un ensemble.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Set`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[ajouter](../../javascript/reference/add-method-set-javascript.md)|Ajoute un élément à un ensemble.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Supprime tous les éléments dans un ensemble.|  
|[supprimer](../../javascript/reference/delete-method-set-javascript.md)|Supprime un élément spécifié dans un ensemble.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Exécute l'action spécifiée pour chaque élément d'un ensemble.|  
|[a](../../javascript/reference/has-method-set-javascript.md)|Retourne `true` si l'ensemble contient un élément spécifié.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Retourne une représentation sous forme de chaîne d'un ensemble.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## Exemple  
 L'exemple suivant montre comment ajouter des membres à un ensemble, puis les récupérer.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]