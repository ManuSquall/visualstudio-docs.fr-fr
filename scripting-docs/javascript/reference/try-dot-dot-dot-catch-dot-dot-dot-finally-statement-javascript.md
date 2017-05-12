---
title: "try...catch...finally, instruction (JavaScript) | Microsoft Docs"
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
  - "try_JavaScriptKeyword"
  - "finally_JavaScriptKeyword"
  - "catch_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "try-catch (gestion des exceptions)"
  - "try-catch (gestion des exceptions), à propos de la gestion des exceptions try-catch"
  - "try-catch (gestion des exceptions), catch (bloc)"
  - "try-catch (gestion des exceptions), finally (bloc)"
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 28
---
# try...catch...finally, instruction (JavaScript)
Installe des blocs de code dans lesquels les erreurs générées dans un bloc sont gérées dans un autre.  Les erreurs générées à l'intérieur du bloc `try` sont interceptées dans le bloc `catch`.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Syntaxe  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## Paramètres  
 `tryStatements`  
 Obligatoire.  Instructions dans lesquelles peut se produire une erreur.  
  
 `exception`  
 Obligatoire.  Tout nom de variable.  La valeur initiale du paramètre `exception` est la valeur de l'erreur générée.  
  
 `catchStatements`  
 Facultatif.  Instructions pour la gestion des erreurs qui se produisent dans les instructions `tryStatements` associées.  
  
 `finallyStatements`  
 Facultatif.  Instructions qui sont exécutées de manière non conditionnelle à la fin du traitement de toutes les autres erreurs.  
  
## Notes  
 L'instruction `try...catch...finally` offre la possibilité de gérer certaines ou l'ensemble des erreurs susceptibles de se produire dans un bloc de code donné, tout en poursuivant l'exécution du code.  Si des erreurs non gérées se produisent, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fournit le message d'erreur normal.  
  
 Le bloc `try` contient le code qui peut provoquer une erreur, tandis que le bloc `catch` contient le code qui gère certaines erreurs ou toutes.  Si une erreur survient dans le bloc `try`, le contrôle du programme est passé au bloc `catch`.  La valeur d'`exception` est la valeur de l'erreur survenue dans le bloc `try`.  Si aucune erreur ne se produit, le code du bloc `catch` n'est jamais exécuté.  
  
 Vous pouvez passer l'erreur jusqu'au niveau suivant à l'aide de l'instruction `throw` pour régénérer l'erreur.  
  
 Une fois que toutes les instructions du bloc `try` ont été exécutées et que la gestion des erreurs a été effectuée dans le bloc `catch`, les instructions du bloc `finally` sont exécutées, qu'une erreur ait été gérée ou non.  Le code du bloc `finally` s'exécute, à moins qu'une erreur non gérée ne se produise \(telle qu'une erreur d'exécution dans le bloc **catch**\).  
  
## Exemple  
 L'exemple suivant provoque la levée d'une exception `ReferenceError` et l'affichage du nom de l'erreur et du message.  
  
```javascript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## Exemple  
 L'exemple suivant montre comment régénérer des erreurs, ainsi que l'exécution des blocs `try…catch` imbriqués.  Quand l'erreur est générée à partir du bloc `try` imbriqué, elle passe au bloc `catch` imbriqué, qui la régénère.  Le bloc `finally` imbriqué s'exécute avant que le bloc `catch` externe ne gère l'erreur et, à la fin, le bloc `finally` externe s'exécute.  
  
```javascript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## Configuration requise  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Depuis le mode des normes d'Internet Explorer 8, le bloc **catch** n'est plus requis pour l'exécution de `finally`.  
  
## Voir aussi  
 [Instruction throw](../../javascript/reference/throw-statement-javascript.md)   
 [Exemple d'application de l'Assistant Configuration Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)