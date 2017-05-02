---
title: "Constante non d&#233;finie (JavaScript) | Microsoft Docs"
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
  - "undefined"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "undefined (propriété)"
ms.assetid: 2a689d7d-00b0-48fb-9c95-5c2867bde006
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Constante non d&#233;finie (JavaScript)
Valeur qui n'a jamais été définie, par exemple une variable qui n'a pas été initialisée.  
  
## Syntaxe  
  
```  
undefined  
```  
  
## Notes  
 La constante `undefined` est un membre de l'objet `Global` et devient disponible lorsque le moteur de script est initialisé.  Lorsqu'une variable a été déclarée sans être initialisée, sa valeur est **undefined**.  
  
 Si une variable n'a pas été déclarée, vous ne pouvez pas la comparer à `undefined`, mais il est possible de comparer son type à la chaîne « undefined ».  
  
 La constante `undefined` est utile lorsque vous testez explicitement une variable ou lui attribuez la valeur undefined.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la constante `undefined`.  
  
```javascript  
// A variable that has not been initialized.  
var declared;  
  
if (declared == undefined)  
    document.write("declared has not been given a value <br/>");  
else  
    document.write("declared has been given a value <br/>");  
  
document.write("typeof declared is " + typeof(declared) + "<br/>");  
  
// An undeclared variable cannot be compared to undefined,  
// so the next line would generate an error.  
// if (notDeclared == undefined);  
  
document.write("typeof notDeclared is " + typeof(notDeclared));  
  
// Output:  
// declared has not been given a value  
// typeof declared is undefined  
// typeof notDeclared is undefined  
```  
  
## Configuration requise  
 La propriété `undefined` a été introduite dans [!INCLUDE[jsv55text](../../javascript/reference/includes/jsv55text-md.md)], et est en lecture seule dans [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)].  
  
 **S'applique à** : [Objet Global](../../javascript/reference/global-object-javascript.md)  
  
## Voir aussi  
 [typeof, opérateur](../../javascript/reference/typeof-operator-decrementjavascript.md)