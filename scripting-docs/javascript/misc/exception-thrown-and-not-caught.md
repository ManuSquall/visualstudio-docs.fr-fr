---
title: Exception levée mais non décelée | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050496"
---
# <a name="exception-thrown-and-not-caught"></a>Exception levée et non interceptée
Vous inclus un `throw` instruction dans votre code, mais il ne se trouvait pas dans un **essayez** bloc, ou il a été associé ne **catch** bloc intercepter l’erreur. Exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et interceptées en dehors de la **essayez** bloquer avec une **intercepter** instruction.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Placez le code peut lever une exception dans un **essayez** bloquer et vérifiez qu’il existe un correspondant **catch** bloc.  
  
- Assurez-vous que votre instruction catch attend la forme correcte d’exception.  
  
- Si l’exception est levée de nouveau, assurez-vous qu’il existe une autre instruction catch correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’erreur](../../javascript/reference/error-object-javascript.md)   
 [Throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)