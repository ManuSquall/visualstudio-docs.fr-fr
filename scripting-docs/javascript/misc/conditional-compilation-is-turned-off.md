---
description: Vous avez tenté d’utiliser une variable de compilation conditionnelle sans activer d’abord la compilation conditionnelle sur.
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
ms.openlocfilehash: ccda9769597d6a981a9277d2b1e1f54b73d6ae18
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571426"
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
 [Compilation conditionnelle](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variables de compilation conditionnelle](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))   
 [@cc_on Gestion](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-cc-on)   
 [@if Gestion](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-if)   
 [@set Gestion](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)
