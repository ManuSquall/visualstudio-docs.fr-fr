---
title: try... catch... finally, instruction (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641729"
---
# <a name="trycatchfinally-statement-javascript"></a>try...catch...finally, instruction (JavaScript)
Installe des blocs de code dans lesquels les erreurs relevées dans un bloc sont gérées dans un autre. Les erreurs levées à l'intérieur du bloc `try` sont interceptées dans le bloc `catch`. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="parameters"></a>Paramètres  
 `tryStatements`  
 Obligatoire. Instructions dans lesquelles peut se produire une erreur.  
  
 `exception`  
 Obligatoire. Tout nom de variable. La valeur initiale de l'argument `exception` est la valeur de l'erreur levée.  
  
 `catchStatements`  
 Facultatif. Instructions pour la gestion des erreurs qui se produisent dans les instructions `tryStatements` associées.  
  
 `finallyStatements`  
 Facultatif. Instructions qui sont exécutées de manière non conditionnelle à la fin du traitement de toutes les autres erreurs.  
  
## <a name="remarks"></a>Remarques  
 L'instruction `try...catch...finally` offre la possibilité de gérer certaines ou toutes les erreurs susceptibles de se produire dans un bloc de code donné, tout en poursuivant l'exécution du code. Si des erreurs non gérées se produisent, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fournit le message d'erreur normal.  
  
 Le bloc `try` contient le code qui peut provoquer une erreur, tandis que le bloc `catch` contient le code qui gère certaines erreurs ou toutes. Si une erreur survient dans le bloc `try`, le contrôle du programme est passé au bloc `catch`. La valeur de `exception` est la valeur de l'erreur levée dans le bloc `try`. Si aucune erreur ne se produit, le code du bloc `catch` n'est jamais exécuté.  
  
 Vous pouvez passer l'erreur jusqu'au niveau suivant à l'aide de l'instruction `throw` pour régénérer l'erreur.  
  
 Une fois que toutes les instructions du bloc `try` ont été exécutées et que la gestion des erreurs a été effectuée dans le bloc `catch`, les instructions du bloc `finally` sont exécutées, qu'une erreur ait été gérée ou non. Le code dans le `finally` bloc est garanti, sauf si une erreur non gérée se produit (par exemple, une erreur d’exécution à l’intérieur de la **catch** bloc).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant provoque la levée d'une exception de `ReferenceError` et l'affichage du message d'erreur et le nom de celle-ci.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment régénérer des erreurs, ainsi que l'exécution des blocs `try...catch` imbriqués. Lorsque l'erreur est générée dans le bloc imbriqué `try`, elle passe au bloc imbriqué `catch`, qui la régénère. Le bloc `finally` imbriqué s'exécute avant que le bloc `catch` externe gère l'erreur, et à la fin, le bloc `finally` externe s'exécute.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  En commençant par le mode standard d’Internet Explorer 8, le **catch** bloc n’est plus nécessaire pour `finally` à exécuter.  
  
## <a name="see-also"></a>Voir aussi  
 [throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [Exemple d’Assistant configuration Script Junkie application](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)