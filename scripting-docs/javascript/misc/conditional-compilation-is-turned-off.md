---
title: La compilation conditionnelle est désactivée | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: da272529768f3227ce6e0ee3e0ebbf086140dd15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816122"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilation conditionnelle est désactivée
Vous avez tenté d’utiliser une variable de compilation conditionnelle sans activer d’abord la compilation conditionnelle sur. L’activation de la compilation conditionnelle indique au [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilateur d’interpréter les identificateurs commençant par @ comme des variables de compilation conditionnelles. Pour ce faire, commencez votre code conditionnel par l’instruction suivante :  
  
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
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Gestion](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Gestion](../../javascript/reference/at-if-statement-javascript.md)   
 [@set Gestion](../../javascript/reference/at-set-statement-javascript.md)