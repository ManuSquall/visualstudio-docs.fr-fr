---
title: switch, instruction (JavaScript) | Documents Microsoft
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
- switch_JavaScriptKeyword
- default_JavaScriptKeyword
- case_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- switch statement
ms.assetid: 61f80e8b-3739-4146-a893-c2832d92b28c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a301fc8bcc72b48c6ba8e999c0ebb70fe9d92b41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641309"
---
# <a name="switch-statement-javascript"></a>switch, instruction (JavaScript)
Active l'exécution d'une ou de plusieurs instructions quand la valeur d'une expression spécifiée correspond à une étiquette donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
switch (expression) {  
    case label :  
        statementlist  
    case label :  
    default :  
        statementlist  
}   
```  
  
## <a name="parameters"></a>Paramètres  
 `expression`  
 L’expression à évaluer.  
  
 `label`  
 Un identificateur pour la correspondance `expression`. Si `label` est un `expression`, l’exécution commence par la `statementlist` immédiatement après le signe deux-points et se poursuit jusqu'à ce qu’il rencontre un `break` instruction, qui est facultative, ou à la fin de la `switch` instruction.  
  
 `statementlist`  
 Une ou plusieurs instructions à exécuter.  
  
## <a name="remarks"></a>Remarques  
 Utilisez le `default` clause pour fournir une instruction à exécuter si aucun de l’étiquette de valeurs correspondances `expression`. Il peut apparaître n’importe où dans le `switch` bloc de code.  
  
 Zéro ou plusieurs `label` blocs peuvent être spécifiés. Si aucun `label` correspond à la valeur de `expression`et un `default` cas n’est pas fourni, les instructions ne sont exécutées.  
  
 L’exécution est acheminé via un `switch` instruction comme suit :  
  
-   Évaluer `expression` et examinez `label` dans l’ordre jusqu'à ce qu’une correspondance est trouvée.  
  
-   Si un `label` valeur est égale à `expression`, exécutez accompagne `statementlist`.  
  
     Poursuivre l’exécution jusqu'à un `break` est rencontrée, ou le `switch` se termine. Cela signifie que plusieurs `label` blocs sont exécutés si une `break` instruction n’est pas utilisée.  
  
-   Si aucun `label` est égal à `expression`, accédez à la `default` cas. S’il existe aucune `default` cas, accédez à la dernière étape.  
  
-   Continuer l’exécution à l’instruction qui suit la fin de la `switch` bloc de code.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant teste un objet pour son type.  
  
```JavaScript  
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
  
## <a name="example"></a>Exemple  
 Le code suivant montre que se passe-t-il si vous n’utilisez pas un `break` instruction.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Instruction if...else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)