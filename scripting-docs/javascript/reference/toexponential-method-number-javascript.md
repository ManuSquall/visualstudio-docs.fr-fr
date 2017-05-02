---
title: "toExponential, m&#233;thode (Number) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential (méthode)"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toExponential, m&#233;thode (Number) (JavaScript)
Représente un nombre en notation exponentielle.  
  
## Syntaxe  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## Paramètres  
 `numObj`  
 Obligatoire.  Objet **Number**.  
  
 `fractionDigits`  
 Facultatif.  Nombre de chiffres après la virgule.  Il doit être compris entre 0 et 20 inclus.  
  
## Valeur de retour  
 Retourne la représentation, sous forme de chaîne, d'un nombre exprimé en notation exponentielle.  La chaîne comporte un chiffre avant la virgule du chiffre et peut contenir le nombre de chiffres indiqué par `fractionDigits` après la virgule.  
  
 Si l'argument `fractionDigits` n'est pas spécifié, la méthode `toExponential` retourne autant de chiffres que nécessaire pour spécifier le nombre de manière unique.  
  
## Exemple  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)  
  
## Voir aussi  
 [toFixed, méthode \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision, méthode \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)