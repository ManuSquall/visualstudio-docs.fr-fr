---
description: Vous avez tenté d’utiliser le mot clé break en dehors d’une boucle.
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
ms.openlocfilehash: d761a1cff89f650e5fc465b6a6aef2713aafb765
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570646"
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
