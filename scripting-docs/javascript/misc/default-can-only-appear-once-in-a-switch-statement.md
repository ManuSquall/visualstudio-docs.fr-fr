---
title: "'default’ne peut apparaître qu’une seule fois dans une instruction’switch' | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862783"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' ne peut apparaître qu'une fois dans une instruction 'switch'
Vous avez tenté d’utiliser l’instruction **par défaut** plusieurs fois dans une instruction switch. Le cas par défaut est toujours la dernière instruction case dans une instruction switch (il s’agit du cas de l’instruction de passage).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez les autres instructions case **par défaut** de votre `switch` instruction (utilisez au plus une instruction case par défaut dans votre instruction switch).  
  
## <a name="see-also"></a>Voir aussi  
 [Switch, instruction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Contrôle du déroulement du programme](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Mots réservés JavaScript](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)