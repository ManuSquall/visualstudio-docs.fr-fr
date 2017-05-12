---
title: "instanceof, op&#233;rateur (JavaScript) | Microsoft Docs"
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
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf (opérateur)"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# instanceof, op&#233;rateur (JavaScript)
Retourne une valeur booléenne indiquant si un objet est une instance d'une classe particulière.  
  
## Syntaxe  
  
```  
  
result = object instanceof class  
```  
  
## Paramètres  
 `result`  
 Requis.  Toute variable.  
  
 `object`  
 Requis.  Toute expression d'objet.  
  
 `class`  
 Requis.  Toute classe d'objets définie.  
  
## Notes  
 L'opérateur `instanceof` retourne la valeur `true` si `object` est une instance de `class`.  Elle retourne `true` si `true` si `class` est présent dans la chaîne prototype de l'objet.  Il retourne la valeur `false` si `object` n'est pas une instance de `class`, ou si `object` a la valeur `null`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'opérateur `instanceof`.  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Voir aussi  
 [Priorité des opérateurs](../../javascript/operator-subtractprecedence-javascript.md)   
 [Résumé des opérateurs \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)