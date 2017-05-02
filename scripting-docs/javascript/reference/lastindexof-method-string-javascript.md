---
title: "lastIndexOf, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndexOf (méthode), chaîne"
  - "chaîne, lastIndexOf (méthode)"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# lastIndexOf, m&#233;thode (String) (JavaScript)
Retourne la dernière occurrence d'une sous\-chaîne de la chaîne.  
  
## Syntaxe  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## Paramètres  
 `strObj`  
 Obligatoire.  Objet `String` ou littéral de chaîne.  
  
 `substring`  
 Obligatoire.  Sous\-chaîne à rechercher.  
  
 `startindex`  
 Facultatif.  Index où commencer la recherche.  Si cette valeur est omise, la recherche commence à la fin de la chaîne.  
  
## Notes  
 La méthode **lastIndexOf** retourne une valeur entière indiquant le début de la sous\-chaîne dans l'objet `String`.  Si la sous\-chaîne est introuvable, une valeur \-1 est retournée.  
  
 Si `startindex` est négatif, `startindex` est considéré comme égal à 0 \(zéro\).  Si l'argument est supérieur à l'index de position de caractère le plus élevé, il est considéré comme l'index le plus grand possible.  
  
 La recherche est effectuée à partir du dernier caractère de la chaîne.  Sinon, cette méthode est identique à **indexOf**.  
  
 L'exemple suivant illustre l'utilisation de la méthode **lastIndexOf**.  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [indexOf, méthode \(String\)](../../javascript/reference/indexof-method-string-javascript.md)