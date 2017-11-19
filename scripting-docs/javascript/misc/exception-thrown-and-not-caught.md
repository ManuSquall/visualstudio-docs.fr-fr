---
title: "Exception levée mais non décelée | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>Exception levée mais non décelée
Vous inclus un `throw` instruction dans votre code, mais il se trouvait pas dans un **essayez** bloc, ou il a été associé ne **catch** bloc pour intercepter l’erreur. Des exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et capturées à l’extérieur de la **essayez** bloc avec un **catch** instruction.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Placez le code peut lever une exception dans un **essayez** bloquer et vérifiez qu’il existe un correspondant **catch** bloc.  
  
-   Assurez-vous que votre instruction catch attend la forme correcte d’exception.  
  
-   Si l’exception est levée de nouveau, vérifiez que s’il existe une autre instruction catch correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Error](../../javascript/reference/error-object-javascript.md)   
 [throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)