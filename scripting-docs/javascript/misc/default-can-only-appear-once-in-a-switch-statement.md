---
title: "'default' ne peut apparaître qu’une seule fois dans une instruction 'switch' | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5d31a74900e8eee5daa97bb7f9af5146b237e04
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842180"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' ne peut apparaître qu'une fois dans une instruction 'switch'
Vous avez tenté d’utiliser le **par défaut** instruction plusieurs fois dans une instruction switch. Le cas par défaut est toujours la dernière instruction case dans une instruction switch (c’est le cas de passage).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez les supplémentaire **par défaut** cas les instructions à partir de votre `switch` instruction (utilisez à la plupart des instruction case par défaut dans votre instruction switch).  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction switch](../../javascript/reference/switch-statement-javascript.md)   
 [Contrôle du flux de programme](../../javascript/controlling-program-flow-javascript.md)   
 [Mots réservés JavaScript](../../javascript/reference/javascript-reserved-words.md)