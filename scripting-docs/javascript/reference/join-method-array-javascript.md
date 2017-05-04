---
title: "join, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join (méthode)"
  - "concaténer des chaînes, join (méthode)"
  - "tableaux (Visual Studio), joindre"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# join, m&#233;thode (Array) (JavaScript)
Ajoute tous les éléments d'un tableau, séparés par la chaîne de séparateur spécifiée.  
  
## Syntaxe  
  
```  
  
arrayObj.join([separator])   
```  
  
## Paramètres  
 `arrayObj`  
 Obligatoire.  Objet `Array`.  
  
 `separator`  
 Facultatif.  Chaîne utilisée pour séparer un élément de tableau du suivant dans l'objet `String` résultant.  Si ce séparateur n'est pas spécifié, les éléments du tableau sont séparés par une virgule.  
  
## Notes  
 Si un élément du tableau a la valeur **undefined** ou `null`, il est traité comme une chaîne vide.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **join**.  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Voir aussi  
 [String, objet](../../javascript/reference/string-object-javascript.md)