---
title: Compilation conditionnelle est désactivée. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8317121b840d82ab12d4a9e1ca50f6680eb1e21d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946574"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilation conditionnelle est désactivée
Vous avez tenté d’utiliser une variable de compilation conditionnelle sans la première compilation conditionnelle tournage sur. L’activation de la compilation conditionnelle indique le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilateur à interpréter les identificateurs commençant par en tant que variables de compilation conditionnelle. Pour cela, vous commencez votre code conditionnel avec l’instruction :  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez l’instruction suivante au début de votre code conditionnel :  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de Compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Instruction](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Instruction](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instruction](../../javascript/reference/at-set-statement-javascript.md)