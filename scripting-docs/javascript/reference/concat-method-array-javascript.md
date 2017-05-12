---
title: "concat, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat (méthode) (array)"
  - "Concat (méthode)"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# concat, m&#233;thode (Array) (JavaScript)
Regroupe au moins deux tableaux.  
  
## Syntaxe  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## Paramètres  
 `array1`  
 Obligatoire.  L'objet `Array` auquel tous les autres tableaux sont concaténés.  
  
 `item1,. . ., itemN`  
 Facultatif.  Éléments supplémentaires à ajouter à la fin du tableau `array1`.  
  
## Notes  
 La méthode `concat` retourne un objet `Array` contenant la concaténation du tableau `array1` et de tout autre élément spécifié.  
  
 Les éléments à ajouter \(*itemN item1*\) au tableau sont insérés dans l'ordre, en commençant par le premier élément de la liste.  Si l'un des éléments est un tableau, son contenu est ajouté à la fin du tableau `array1`.  Si l'élément n'est pas un tableau, il est ajouté à la fin du tableau en tant qu'élément unique de tableau.  
  
 Les éléments des tableaux sources sont copiés dans le nouveau tableau de la manière suivante :  
  
-   Si une référence d'objet copiée dans le nouveau tableau provient de l'un des tableaux en cours de concaténation, la référence d'objet continue à pointer vers le même objet.  Tout changement apporté au nouveau tableau est répercuté dans le tableau d'origine et réciproquement.  
  
-   Si un nombre ou une valeur numérique est ajoutée au nouveau tableau, seule la valeur est copiée.  La modification de la valeur dans un tableau n'affecte pas la valeur de l'autre tableau.  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode `concat` quand elle est utilisée avec un tableau :  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [Méthode concat \(Chaîne\)](../../javascript/reference/concat-method-string-javascript.md)   
 [join, méthode \(Array\)](../../javascript/reference/join-method-array-javascript.md)