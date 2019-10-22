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
ms.openlocfilehash: aca09fe3b516fbb8f27def982bf34a22d33d4ada
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572362"
---
# <a name="cannot-assign-to-a-function-result"></a>Impossible d'affecter à un résultat de fonction
Vous avez tenté d’assigner une valeur à un résultat de fonction. Le résultat d’une fonction peut être assigné à une variable, mais il ne peut pas être utilisé en tant que variable. Si vous souhaitez assigner une nouvelle valeur à la fonction elle-même, omettez les parenthèses (opérateur d’appel de fonction). L’exemple suivant illustre une situation dans laquelle cette erreur est générée.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- N’utilisez pas la valeur d’un résultat d’appel de fonction comme un que vous pouvez *assigner à*. Vous pouvez cependant assigner le résultat de l’appel de fonction *à une variable* .  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
- Vous pouvez également assigner la fonction elle-même (et non sa valeur de retour) à une variable.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)    
 [Écriture de code JavaScript](../../javascript/writing-javascript-code.md)    
 [Fonctions](../../javascript/functions-javascript.md)