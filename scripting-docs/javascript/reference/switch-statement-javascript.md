---
title: "switch, instruction (JavaScript) | Microsoft Docs"
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
  - "switch_JavaScriptKeyword"
  - "default_JavaScriptKeyword"
  - "case_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "switch (instruction)"
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# switch, instruction (JavaScript)
Active l'exécution d'une ou de plusieurs instructions quand la valeur d'une expression spécifiée correspond à une étiquette donnée.  
  
## Syntaxe  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## Paramètres  
 `expression`  
 Expression à évaluer.  
  
 `label`  
 Identificateur à comparer à une `expression`.  Si l'argument `label` est une `expression`, l'exécution commence par la `statementlist` immédiatement après le signe deux\-points et se poursuit jusqu'à ce qu'elle rencontre une instruction `break`, qui est facultative, ou à la fin de l'instruction `switch`.  
  
 `statementlist`  
 Une ou plusieurs instructions à exécuter.  
  
## Notes  
 Utilisez la clause `default` pour fournir une instruction à exécuter si aucune des valeurs d'étiquette ne correspond à `expression`.  Elle peut figurer n'importe où dans le bloc de code `switch`.  
  
 Aucun ou plusieurs blocs `label` peuvent être spécifiés.  Si aucun argument `label` ne correspond à la valeur `expression` et qu'aucun cas `default` n'est fourni, aucune instruction n'est exécutée.  
  
 L'exécution d'une instruction `switch` se déroule comme suit :  
  
-   Évaluation de la valeur `expression` et recherche d'une correspondance dans `label`, dans l'ordre.  
  
-   Si une valeur `label` est égale à `expression`, exécution de la `statementlist`qui l'accompagne.  
  
     Poursuite de l'exécution jusqu'à la rencontre d'une instruction `break` ou jusqu'à la fin d'une instruction `switch`.  Cela signifie que plusieurs blocs `label` sont exécutés si une instruction `break` n'est pas utilisée.  
  
-   Si aucun argument `label` n'est égal à `expression`, saut jusqu'au cas `default`.  En l'absence d'une clause `default`, saut jusqu'à la dernière étape.  
  
-   Poursuite de l'exécution à partir de l'instruction qui suit la fin du bloc de code `switch`.  
  
## Exemple  
 L'exemple suivant teste le type d'un objet.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
            break;  
        case Number:  
            document.write("Object is a Number.");  
            break;  
        case String:  
            document.write("Object is a String.");  
            break;  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.  
  
// Output when obj is a Number:  
// Object is a Number.  
  
// Output when obj is a String:  
// Object is a String.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Exemple  
 Le code suivant illustre ce qui se produit si vous n'utilisez pas une instruction `break`.  
  
```javascript  
function MyObjectType(obj) {  
    switch (obj.constructor) {  
        case Date:  
            document.write("Object is a Date.");  
        case Number:  
            document.write("Object is a Number.");  
        case String:  
            document.write("Object is a String.");  
        default:  
            document.write("Object is unknown.");  
    }  
}  
  
// Output when obj is a Date:  
// Object is a Date.Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a Number:  
// Object is a Number.Object is a String.Object is unknown.  
  
// Output when obj is a String:  
// Object is a String.Object is unknown.  
  
// Output when obj is something other than a Date, Number, or String:  
// Object is unknown.  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [if...else, instruction](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)