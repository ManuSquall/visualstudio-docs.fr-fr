---
title: Peut &#39; t ont &#39; arrêt &#39; en dehors de la boucle | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633149"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Peut &#39; t ont &#39; arrêt &#39; en dehors de la boucle
Vous avez tenté d’utiliser le **saut** (mot clé) en dehors d’une boucle. Le **saut** mot clé est utilisé pour mettre fin à une boucle ou `switch` instruction. Il doit être incorporé dans le corps d’une boucle ou `switch` instruction. Toutefois, un **étiquette** peut suivre le mot clé break.  
  
```  
break labelname;  
```  
  
 Vous devez uniquement la forme étiquetée de la **saut** mot clé lorsque vous utilisez des boucles imbriquées ou `switch` instructions et la nécessité d’interrompre une boucle qui n’est pas le plus profond.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que le **saut** mot clé apparaît à l’intérieur d’une instruction de boucle ou de commutateur englobante.  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)