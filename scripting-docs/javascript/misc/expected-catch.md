---
title: "'Catch’attendu | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9950573e7bbeefe3594d77df2ae41c12f77ed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816682"
---
# <a name="expected-catch"></a>'catch' attendu
Vous avez utilisé le bloc **try** de gestion des exceptions, mais n’avez pas écrit l’instruction **catch** associée. Le mécanisme de gestion des exceptions exige que le code qui peut échouer, ainsi que le code qui ne doit pas s’exécuter si une exception se produit, sont encapsulés à l’intérieur d’un bloc **try** . Les exceptions sont levées à partir du bloc **try** à l’aide de l’instruction **throw** et interceptées en dehors du bloc **try** avec une ou plusieurs instructions **catch** .  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez le bloc **catch** associé.  
  
- Essayez d’utiliser un bloc **finally** au lieu d’un bloc **catch** .  
  
## <a name="see-also"></a>Voir aussi  
 [essayer... catch... Finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objet Error](../../javascript/reference/error-object-javascript.md)