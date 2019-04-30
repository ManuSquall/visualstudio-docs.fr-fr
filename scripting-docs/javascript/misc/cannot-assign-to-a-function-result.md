---
title: Impossible d’assigner à un résultat de fonction | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226056f139e45f432d757aff8f8774b013742de3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946600"
---
# <a name="cannot-assign-to-a-function-result"></a>Impossible d'affecter à un résultat de fonction
Vous avez tenté d’assigner une valeur à un résultat de fonction. Le résultat d’une fonction peut être assigné à une variable, mais il ne peut pas être utilisé en tant que variable. Si vous souhaitez affecter une nouvelle valeur à la fonction elle-même, omettre les parenthèses (l’opérateur d’appel de fonction). L’exemple suivant illustre une situation dans laquelle cette erreur est générée.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- N’utilisez pas la valeur d’un résultat d’appel de fonction en tant que quelque chose que vous pouvez *affecter à*. Vous pouvez affecter le résultat de l’appel de fonction *à une variable* si.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Ou bien, vous pouvez affecter la fonction elle-même (et pas sa valeur de retour) à une variable.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Écriture de Code JavaScript](../../javascript/writing-javascript-code.md)   
 [Fonctions](../../javascript/functions-javascript.md)