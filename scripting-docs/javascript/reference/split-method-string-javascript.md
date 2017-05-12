---
title: "split, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split (méthode)"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# split, m&#233;thode (String) (JavaScript)
Fractionner une chaîne en sous\-chaînes à l'aide du séparateur spécifié et les retourner sous la forme d'un tableau.  
  
## Syntaxe  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## Paramètres  
 `stringObj`  
 Obligatoire.  Objet `String` ou littéral de chaîne à fractionner.  Cet objet n'est pas modifié par la méthode **split**.  
  
 `separator`  
 Facultatif.  Chaîne ou objet **Regular Expression** qui identifie un ou plusieurs caractères à utiliser pour fractionner la chaîne.  Si cet argument est omis, la méthode retourne un tableau à un seul élément contenant la chaîne entière.  
  
 `limit`  
 Facultatif.  Valeur utilisée pour limiter le nombre d'éléments retournés dans le tableau.  
  
## Valeur de retour  
 Le résultat de la méthode **split** est un tableau de chaînes fractionné à chaque endroit où `separator` apparaît dans `stringObj`.  L'argument `separator` n'est pas retourné comme partie d'un élément du tableau.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode **split**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [Méthode concat \(Chaîne\)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp, objet](../../javascript/reference/regexp-object-javascript.md)   
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Défilement, panoramique et zoom d'exemple d'application](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)