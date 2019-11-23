---
title: "'default’ne peut apparaître qu’une seule fois dans une instruction’switch' | Microsoft Docs"
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
ms.openlocfilehash: 90652e44a4bd0362f679be71d0d6401165487aec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572880"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' ne peut apparaître qu'une fois dans une instruction 'switch'
Vous avez tenté d’utiliser l’instruction **par défaut** plusieurs fois dans une instruction switch. Le cas par défaut est toujours la dernière instruction case dans une instruction switch (il s’agit du cas de l’instruction de passage).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez les autres instructions case **par défaut** de votre instruction `switch` (utilisez au plus une instruction case par défaut dans votre instruction switch).  
  
## <a name="see-also"></a>Voir aussi  
 [instruction switch](../../javascript/reference/switch-statement-javascript.md)   
 [Contrôle du déroulement du programme](../../javascript/controlling-program-flow-javascript.md)   
 [Mots réservés JavaScript](../../javascript/reference/javascript-reserved-words.md)