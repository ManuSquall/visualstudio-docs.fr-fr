---
title: Ne peut pas avoir 'break' en dehors de la boucle | Microsoft Docs
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
ms.openlocfilehash: 53f32da997b775e01959df5abc7e72fb55c1b194
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345043"
---
# <a name="cant-have-break-outside-of-loop"></a>Impossible d'utiliser une instruction 'break' en dehors d'une boucle
Vous avez tenté d’utiliser le **saut** mot clé en dehors d’une boucle. Le **saut** mot clé est utilisé pour mettre fin à une boucle ou `switch` instruction. Il doit être incorporé dans le corps d’une boucle ou `switch` instruction. Toutefois, un **étiquette** pouvez suivre le mot clé break.  
  
```js
break labelname;  
```  
  
 Il vous suffit le formulaire étiqueté de la **saut** mot clé lorsque vous utilisez des boucles imbriquées ou `switch` instructions et devoir quitter une boucle qui n’est pas le plus profond.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que le **saut** mot clé apparaît à l’intérieur d’une instruction de boucle ou switch englobante.  
  
## <a name="see-also"></a>Voir aussi  
 [break, instruction](../../javascript/reference/break-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)