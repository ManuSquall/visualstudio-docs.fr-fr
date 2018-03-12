---
title: Attendu &#39; @&#39; | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f007129aa8da3ac49112fbc83b7abd31e4356c4f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939"></a>Attendu &#39; @&#39;
Vous avez tenté de créer une variable qui doit être utilisé avec les instructions de compilation conditionnelle à l’aide de la `@set` instruction, mais le n'a pas placé un signe «**@**» avant le nom de variable.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter un signe «**@**« immédiatement avant le nom de variable. Exemple :  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [@setInstruction](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilation conditionnelle](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilation conditionnelle](../../javascript/advanced/conditional-compilation-variables-javascript.md)