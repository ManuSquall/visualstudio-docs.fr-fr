---
title: Fonction attendue | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349801"
---
# <a name="function-expected"></a>Fonction attendue
Soit vous avez tenté d’appeler une de la **prototype de fonction** méthodes sur un objet qui n’était pas un `Function` objet, ou utilisé un objet dans un contexte d’appel de fonction. Par exemple, le code suivant génère cette erreur, car **exemple** n’est pas une fonction.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Appelez uniquement **prototype de fonction** méthodes sur `Function` objets.  
  
-   Vérifiez que vous utilisez l’opérateur d’appel de fonction `()` pour appeler les fonctions uniquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)