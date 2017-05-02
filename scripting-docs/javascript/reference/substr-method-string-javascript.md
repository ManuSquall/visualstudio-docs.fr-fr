---
title: "substr, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr (méthode)"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# substr, m&#233;thode (String) (JavaScript)
Obtient une sous\-chaîne débutant à la position spécifiée et ayant la longueur déterminée.  
  
## Syntaxe  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## Paramètres  
 `stringvar`  
 Obligatoire.  Littéral de chaîne ou objet `String` dont la sous\-chaîne est récupérée.  
  
 `start`  
 Obligatoire.  Position de début de la sous\-chaîne désirée.  L'index du premier caractère de la chaîne est zéro.  
  
 `length`  
 Facultatif.  Nombre de caractères à inclure dans la sous\-chaîne retournée.  
  
## Notes  
 Si la valeur `length` est nulle ou négative, une chaîne vide est retournée.  Si elle n'est pas spécifiée, la sous\-chaîne continue jusqu'à la fin de `stringvar`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `substr`.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [substring, méthode \(String\)](../../javascript/reference/substring-method-string-javascript.md)