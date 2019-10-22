---
title: La compilation conditionnelle est désactivée | Microsoft Docs
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
ms.openlocfilehash: 56621d6f7fcc195a4ece7654adeafd1096c37e8b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572932"
---
# <a name="conditional-compilation-is-turned-off"></a>La compilation conditionnelle est désactivée
Vous avez tenté d’utiliser une variable de compilation conditionnelle sans activer d’abord la compilation conditionnelle sur. L’activation de la compilation conditionnelle indique au compilateur [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] d’interpréter les identificateurs commençant par @ comme des variables de compilation conditionnelles. Pour ce faire, commencez votre code conditionnel par l’instruction suivante :  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez l’instruction suivante au début de votre code conditionnel :  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de [compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)    
 [instruction @cc_on](../../javascript/reference/at-cc-on-statement-javascript.md)    
 [instruction @if](../../javascript/reference/at-if-statement-javascript.md)    
 [@set Instruction](../../javascript/reference/at-set-statement-javascript.md)