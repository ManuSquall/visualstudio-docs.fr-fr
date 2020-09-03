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
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817656"
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
 [Break (instruction)](../../javascript/reference/break-statement-javascript.md)   
 [Contrôle du déroulement du programme](../../javascript/controlling-program-flow-javascript.md)   
 [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)