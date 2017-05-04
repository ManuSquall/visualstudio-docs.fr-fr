---
title: "findIndex, m&#233;thode (Array) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# findIndex, m&#233;thode (Array) (JavaScript)
Retourne une valeur d'index pour le premier élément du tableau qui répond aux critères de test spécifiés dans une fonction de rappel.  
  
## Syntaxe  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### Paramètres  
 `arrayObj`  
 Obligatoire.  Objet Array.  
  
 `callbackfn`  
 Obligatoire.  Fonction de rappel pour tester chaque élément dans le tableau.  
  
 `thisArg`  
 Facultatif.  Spécifie l'objet `this` dans la fonction de rappel.  Si aucune valeur n'est spécifiée, l'objet `this` n'est pas défini.  
  
## Notes  
 La méthode `findIndex` appelle la fonction de rappel une fois pour chaque élément du tableau, dans l'ordre croissant, jusqu'à ce qu'un élément retourne `true`.  Dès qu'un élément retourne true, `findIndex` retourne la valeur d'index de l'élément qui retourne la valeur true.  Si aucun élément du tableau ne retourne true, `findIndex` retourne \-1.  
  
 `findIndex` ne mute pas l'objet Array.  
  
## Syntaxe de la fonction de rappel  
 La syntaxe de la fonction de rappel se présente comme suit :  
  
 `function callbackfn(value, index, thisArg)`  
  
 Vous pouvez déclarer la fonction de rappel à l'aide de trois paramètres au maximum.  
  
 Les paramètres de la fonction de rappel se présentent comme suit.  
  
|Argument de rappel|Définition|  
|------------------------|----------------|  
|`value`|Valeur de l'élément de tableau.|  
|`index`|Index numérique de l'élément de tableau.|  
|`arrayObj`|Objet Array à traverser.|  
  
## Exemple  
 Dans l'exemple suivant, la fonction de rappel vérifie si chaque élément du tableau est égal à 2.  
  
```javascript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## Exemple  
 L'exemple suivant utilise la syntaxe de fonction Arrow pour tester chaque élément.  Dans cet exemple, aucun élément ne retourne `true`, et `findIndex` retourne \-1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]