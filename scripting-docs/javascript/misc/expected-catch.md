---
title: "'Catch’attendu | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573431"
---
# <a name="expected-catch"></a>'catch' attendu
Vous avez utilisé le bloc **try** de gestion des exceptions, mais n’avez pas écrit l’instruction **catch** associée. Le mécanisme de gestion des exceptions exige que le code qui peut échouer, ainsi que le code qui ne doit pas s’exécuter si une exception se produit, sont encapsulés à l’intérieur d’un bloc **try** . Les exceptions sont levées à partir du bloc **try** à l’aide de l’instruction **throw** et interceptées en dehors du bloc **try** avec une ou plusieurs instructions **catch** .  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez le bloc **catch** associé.  
  
- Essayez d’utiliser un bloc **finally** au lieu d’un bloc **catch** .  
  
## <a name="see-also"></a>Voir aussi  
 [essayer... catch... Finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)    
 [Objet Error](../../javascript/reference/error-object-javascript.md)