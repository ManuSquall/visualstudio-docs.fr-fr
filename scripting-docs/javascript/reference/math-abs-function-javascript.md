---
title: "Math.abs, fonction (JavaScript) | Microsoft Docs"
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
  - "abs"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "valeurs absolues, calcul"
  - "valeurs absolues"
  - "expressions numériques"
  - "abs (méthode)"
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Math.abs, fonction (JavaScript)
Retourne la valeur absolue d'un nombre \(sa valeur sans tenir compte du fait qu'il soit positif ou négatif\).  Par exemple, \-5 et 5 ont une valeur absolue identique.  
  
## Syntaxe  
  
```  
Math.abs(number)  
```  
  
#### Paramètres  
 L'argument `number` requis est une expression numérique pour laquelle la valeur absolue est nécessaire.  
  
## Valeur de retour  
 Valeur absolue de l'argument `number`.  
  
## Exemple  
 L'exemple ci\-dessous illustre l'utilisation de la fonction `abs` :  
  
```javascript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S'applique à** : [Objet Math](../../javascript/reference/math-object-javascript.md)  
  
## Voir aussi  
 [Objet Math](../../javascript/reference/math-object-javascript.md)