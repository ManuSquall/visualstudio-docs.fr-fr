---
title: Exception levée mais non décelée | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349034"
---
# <a name="exception-thrown-and-not-caught"></a>Exception levée mais non décelée
Vous inclus un `throw` instruction dans votre code, mais il ne se trouvait pas dans un **essayez** bloc, ou il a été associé ne **catch** bloc intercepter l’erreur. Exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et interceptées en dehors de la **essayez** bloquer avec une **intercepter** instruction.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Placez le code peut lever une exception dans un **essayez** bloquer et vérifiez qu’il existe un correspondant **catch** bloc.  
  
-   Assurez-vous que votre instruction catch attend la forme correcte d’exception.  
  
-   Si l’exception est levée de nouveau, assurez-vous qu’il existe une autre instruction catch correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’erreur](../../javascript/reference/error-object-javascript.md)   
 [Throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)