---
title: "concat, m&#233;thode (String) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat (méthode) (String)"
  - "Concat (méthode)"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# concat, m&#233;thode (String) (JavaScript)
Retourne une chaîne contenant la concaténation d'au moins deux chaînes.  
  
## Syntaxe  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## Paramètres  
 `string1`  
 Obligatoire.  Objet `String` ou littéral de chaîne avec lequel les autres chaînes spécifiées sont concaténées.  
  
 `string2,. . ., stringN`  
 Facultatif.  Chaînes à ajouter à la fin de `string1`.  
  
## Notes  
 Le résultat de la méthode `concat` équivaut à : `result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`.  La modification d'une valeur dans une chaîne source ou de résultat n'a aucune répercussion sur la valeur contenue dans l'autre chaîne.  Si l'un des arguments ne constitue pas une chaîne, il est converti en chaîne avant d'être concaténé à la chaîne `string1`.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de la méthode `concat` avec une chaîne :  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **S'applique à** : [String, objet](../../javascript/reference/string-object-javascript.md)  
  
## Voir aussi  
 [Opérateur d'addition \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)