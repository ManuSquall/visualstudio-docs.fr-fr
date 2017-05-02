---
title: "toPrecision, m&#233;thode (Number) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision (méthode)"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toPrecision, m&#233;thode (Number) (JavaScript)
Représente un nombre en notation exponentielle ou avec une virgule fixe, avec le nombre spécifié de chiffres.  
  
## Syntaxe  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## Paramètres  
 `numObj`  
 Obligatoire.  Un objet `Number`.  
  
 `precision`  
 Facultatif.  Le nombre de chiffres significatifs.  Il doit être compris entre 1 et 21 inclus.  
  
## Valeur de retour  
 Pour les nombres exprimés en notation exponentielle, la méthode retourne le nombre de chiffres après la virgule indiqué par `precision` \- 1.  Pour les nombres à virgule fixe, la méthode retourne le nombre de chiffres significatifs indiqué par `precision`.  
  
 Si la valeur `precision` n'est pas spécifiée ou si elle est égale à **non définie**, c'est la méthode **toString** qui est appelée à la place.  
  
## Exemple  
 Le code suivant montre comment utiliser `toPrecision`.  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)  
  
## Voir aussi  
 [toFixed, méthode \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential, méthode \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)