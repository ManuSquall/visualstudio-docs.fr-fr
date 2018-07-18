---
title: Compilation conditionnelle est désactivée | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633109"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilation conditionnelle est désactivée
Vous avez tenté d’utiliser une variable de compilation conditionnelle sans activer la compilation conditionnelle première sur. L’activation de la compilation conditionnelle indique le [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilateur à interpréter les identificateurs commençant par @ comme des variables de compilation conditionnelle. Pour cela, vous commencez votre code conditionnel avec l’instruction :  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez l’instruction suivante au début de votre code conditionnel :  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de Compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstruction](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@ifInstruction](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Instruction](../../javascript/reference/at-set-statement-javascript.md)