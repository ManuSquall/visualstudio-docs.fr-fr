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
ms.openlocfilehash: e1e34be9f8eab5171af0e2553d5777b0958bf3c2
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840868"
---
# <a name="exception-thrown-and-not-caught"></a>Exception levée et non interceptée
Vous inclus un `throw` instruction dans votre code, mais il ne se trouvait pas dans un **essayez** bloc, ou il a été associé ne **catch** bloc intercepter l’erreur. Exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et interceptées en dehors de la **essayez** bloquer avec une **intercepter** instruction.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Placez le code peut lever une exception dans un **essayez** bloquer et vérifiez qu’il existe un correspondant **catch** bloc.  
  
-   Assurez-vous que votre instruction catch attend la forme correcte d’exception.  
  
-   Si l’exception est levée de nouveau, assurez-vous qu’il existe une autre instruction catch correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’erreur](../../javascript/reference/error-object-javascript.md)   
 [Throw (instruction)](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)