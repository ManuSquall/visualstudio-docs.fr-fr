---
title: "&#39; par défaut &#39; ne peut apparaître qu’une seule fois dans un &#39; commutateur &#39; instruction | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e60dd1ce6b4102ab856cd3d45416175c7030e8d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="39default39-can-only-appear-once-in-a-39switch39-statement"></a>&#39; par défaut &#39; ne peut apparaître qu’une seule fois dans un &#39; commutateur &#39; instruction
Vous avez tenté d’utiliser le **par défaut** instruction plusieurs fois dans une instruction switch. Le cas par défaut est toujours la dernière instruction case dans une instruction switch (c’est le cas de passage).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimer les supplémentaire **par défaut** cas les instructions à partir de votre `switch` instruction (utilisez à la plupart des instruction case une valeur par défaut dans votre instruction switch).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction switch](../../javascript/reference/switch-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Mots réservés JavaScript](../../javascript/reference/javascript-reserved-words.md)