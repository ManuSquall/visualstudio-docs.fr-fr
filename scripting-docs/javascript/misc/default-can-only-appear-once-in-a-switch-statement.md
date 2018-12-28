---
title: "'default' ne peut apparaître qu’une seule fois dans une instruction 'switch' | Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4f254825e27793999932b772ac4bc2512908fae
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803881"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' ne peut apparaître qu'une fois dans une instruction 'switch'
Vous avez tenté d’utiliser le **par défaut** instruction plusieurs fois dans une instruction switch. Le cas par défaut est toujours la dernière instruction case dans une instruction switch (c’est le cas de passage).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez les supplémentaire **par défaut** cas les instructions à partir de votre `switch` instruction (utilisez à la plupart des instruction case par défaut dans votre instruction switch).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction switch](../../javascript/reference/switch-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Mots réservés JavaScript](../../javascript/reference/javascript-reserved-words.md)