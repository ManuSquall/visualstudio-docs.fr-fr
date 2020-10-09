---
title: Impossible d’avoir’Break’en dehors de Loop | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee177c8070fc5af8123d7fd78e69b1f767a5b700
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862797"
---
# <a name="cant-have-break-outside-of-loop"></a>Impossible d'utiliser une instruction 'break' en dehors d'une boucle
Vous avez tenté d’utiliser le mot clé **break** en dehors d’une boucle. Le mot clé **break** est utilisé pour mettre fin à une boucle ou une `switch` instruction. Elle doit être incorporée dans le corps d’une boucle ou d’une `switch` instruction. Toutefois, une **étiquette** peut suivre le mot clé Break.  
  
```js
break labelname;  
```  
  
 Vous avez uniquement besoin de la forme étiquetée du mot clé **break** lorsque vous utilisez des instructions ou des boucles imbriquées `switch` et que vous devez quitter une boucle qui n’est pas la plus profonde.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous que le mot clé **break** apparaît dans une boucle englobante ou une instruction switch.  
  
## <a name="see-also"></a>Voir aussi  
 [Break (instruction)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Contrôle du déroulement du programme](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Résolution des problèmes liés aux scripts](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)