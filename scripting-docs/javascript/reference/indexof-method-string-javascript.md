---
title: "indexOf, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf (méthode), de type chaîne"
  - "de type chaîne, indexOf (méthode)"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# indexOf, m&#233;thode (String) (JavaScript)
Retourne la position de la première occurrence d'une sous\-chaîne.  
  
## Syntaxe  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## Paramètres  
 `strObj`  
 Obligatoire.  Objet `String` ou littéral de chaîne.  
  
 `subString`  
 Obligatoire.  Sous\-chaîne à rechercher dans la chaîne  
  
 `startIndex`  
 Facultatif.  Index à partir duquel commencer la recherche de l'objet `String`.  Si ce paramètre est omis, la recherche commence au début de la chaîne.  
  
## Notes  
 La méthode **indexOf** retourne le début de la sous\-chaîne dans l'objet `String`.  Si la sous\-chaîne est introuvable, la valeur \-1 est retournée.  
  
 Si `startindex` est négatif, `startindex` est considéré comme égal à 0 \(zéro\).  S'il est supérieur à l'index le plus élevé, il est considéré comme l'index le plus grand possible.  
  
 La recherche est effectuée de gauche à droite.  Sinon, cette méthode est identique à **lastIndexOf**.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **indexOf** :  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [Méthode lastIndexOf \(Chaîne\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [Défilement, panoramique et zoom d'exemple d'application](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)