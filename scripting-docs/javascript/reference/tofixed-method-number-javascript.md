---
title: "toFixed, m&#233;thode (Number) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed (méthode)"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# toFixed, m&#233;thode (Number) (JavaScript)
Représente un nombre à virgule fixe.  
  
## Syntaxe  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## Paramètres  
 `numObj`  
 Objet `Number` requis.  
  
 `fractionDigits`  
 Optionnel.  Nombre de chiffres après la virgule décimale.  Il doit être compris entre 0 et 20 inclus.  
  
## Valeur de retour  
 Retourne une représentation sous forme de chaîne d'un nombre à virgule fixe, contenant des chiffres `fractionDigits` après la virgule décimale.  
  
 Si le paramètre `fractionDigits` n'est pas spécifié ou qu'il présente la valeur **undefined**, la valeur par défaut est zéro.  
  
## Exemple  
 Le code suivant montre comment utiliser `toFixed` :  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [Number, objet](../../javascript/reference/number-object-javascript.md)  
  
## Voir aussi  
 [toExponential, méthode \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision, méthode \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)