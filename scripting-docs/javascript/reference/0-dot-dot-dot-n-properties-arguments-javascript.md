---
title: "0...n, propri&#233;t&#233;s (arguments) (JavaScript) | Microsoft Docs"
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
  - "0...n"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Propriétés 0...n"
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 0...n, propri&#233;t&#233;s (arguments) (JavaScript)
Retourne la valeur réelle d'arguments spécifiques à partir d'un objet **arguments** retourné par la propriété **arguments** de la fonction en cours d'exécution.  
  
## Syntaxe  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## Paramètres  
 *function*  
 Facultatif.  Nom de l'objet `Function` en cours d'exécution.  
  
 0, 1, 2, *, n*  
 Obligatoire.  Entier non négatif compris dans la plage de 0 à *n*, où 0 représente le premier argument et *n* l'argument final.  La valeur de l'argument final *n* est **arguments.length\-1**.  
  
## Notes  
 Les valeurs retournées par les propriétés 0 .  .  .  n sont les valeurs réelles passées à la fonction en cours d'exécution.  Même s'ils ne constituent pas réellement un tableau d'arguments, les différents arguments qui composent l'objet **arguments** sont accessibles de la même manière que les éléments d'un tableau.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation des propriétés **0 . . .**  ***n*** de l'objet **arguments**.  Pour comprendre parfaitement l'exemple, passez un ou plusieurs arguments à la fonction :  
  
```javascript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## Configuration requise  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **S'applique à** : [arguments, objet](../../javascript/reference/arguments-object-javascript.md)&#124; [Objet de function](../../javascript/reference/function-object-javascript.md)  
  
## Voir aussi  
 [length, propriété \(arguments\)](../../javascript/reference/length-property-arguments-javascript.md)   
 [Propriété length \(Fonction\)](../../javascript/reference/length-property-function-javascript.md)