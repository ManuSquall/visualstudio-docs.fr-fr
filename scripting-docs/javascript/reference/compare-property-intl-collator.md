---
title: "compare, propri&#233;t&#233; (Intl.Collator) | Microsoft Docs"
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
ms.assetid: 59f274dc-6e52-4344-8d5c-b9f0000b66e0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# compare, propri&#233;t&#233; (Intl.Collator)
Retourne une fonction qui compare deux chaînes à l'aide de l'ordre de tri de l'assembleur.  
  
## Syntaxe  
  
```javascript  
collatorObj.compare  
```  
  
#### Paramètres  
 `collatorObj`  
 Requis.  Le nom de l'objet `Collator` à utiliser pour la comparaison.  
  
## Notes  
 La fonction retournée par la propriété `compare` accepte deux arguments, `x` et `y`, et retourne le résultat d'une comparaison spécifique aux paramètres régionaux de `x` et `y` en utilisant les options spécifiées dans l'objet `Collator`.  
  
 Le résultat de la comparaison sera :  
  
-   \-1 si `x` est placé avant `y` dans l'ordre de tri.  
  
-   0 \(zéro\) si `x` est égal à `y` dans l'ordre de tri.  
  
-   1 si `x` est placé après `y` dans l'ordre de tri.  
  
## Exemple  
 L'exemple suivant crée un objet `Collator` et effectue une comparaison.  
  
```javascript  
var co = new Intl.Collator(["de-DE-u-co-phonebk"]);  
  
if (console && console.log) {  
    console.log(co.compare("a", "b")); // Returns -1  
}  
```  
  
## Exemple  
 L'exemple suivant utilise des objets `Collator` pour trier un tableau.  Cet exemple illustre les différences spécifiques aux paramètres régionaux.  
  
```javascript  
var co1 = new Intl.Collator(["de-DE-u-co-phonebk"]);  
var co2 = new Intl.Collator(["de-DE"]);  
var co3 = new Intl.Collator(["en-US"]);  
  
var arr = ["ä", "ad", "af", "a"];  
  
if (console && console.log) {  
    console.log(arr.sort(co1.compare));  // Returns a,ad,ä,af  
    console.log(arr.sort(co2.compare));  // Returns a,ä,ad,af  
    console.log(arr.sort(co3.compare));  // Returns a,ä,ad,af  
}  
```  
  
## Exemple  
 L'exemple suivant utilise un objet `Collator` pour rechercher une chaîne.  
  
```javascript  
// String to search  
var arr = ["ä", "ad", "af", "a"];  
// String searched for  
var s = "af";  
  
var co = new Intl.Collator("de-DE", { usage: "search" });  
var matches = arr.filter(function (i) {  
    return co.compare(i, s) === 0;  
});  
  
if (console && console.log) {  
    console.log(matches);  // Returns af  
}  
```  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Voir aussi  
 [Intl.Collator, objet](../../javascript/reference/intl-collator-object-javascript.md)