---
title: Attendu &#39; catch &#39; | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>Attendu &#39; catch &#39;
Vous avez utilisé la gestion des exceptions **essayez** bloque, mais n’avez pas écrit associé **catch** instruction. Le mécanisme de gestion des exceptions requiert que le code peut échouer, ainsi que le code ne doit pas s’exécuter si une exception se produit, encapsulés dans un **essayez** bloc. Des exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et capturées à l’extérieur de la **essayez** bloc avec un ou plusieurs **catch**instructions.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter au **catch** bloc.  
  
-   Essayez d’utiliser un **enfin** bloquer au lieu d’un **catch** bloc.  
  
## <a name="see-also"></a>Voir aussi  
 [try... catch... finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objet Error](../../javascript/reference/error-object-javascript.md)