---
title: "'Catch' attendu | Microsoft Docs"
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
ms.openlocfilehash: 4a25f72fccfd072243d6d0fdfd1d311c1a3bb6f4
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841446"
---
# <a name="expected-catch"></a>'catch' attendu
Vous avez utilisé la gestion des exceptions **essayez** bloquer, mais n’avez pas écrit associé **catch** instruction. Le mécanisme de gestion des exceptions requiert que le code peut échouer, ainsi que le code qui ne doit pas s’exécuter si une exception se produit, être encapsulées à l’intérieur d’un **essayez** bloc. Exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et interceptées en dehors de la **essayez** bloc avec un ou plusieurs **catch**instructions.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter associé **catch** bloc.  
  
-   Essayez d’utiliser un **enfin** bloquer au lieu d’un **catch** bloc.  
  
## <a name="see-also"></a>Voir aussi  
 [try... catch... finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objet Error](../../javascript/reference/error-object-javascript.md)