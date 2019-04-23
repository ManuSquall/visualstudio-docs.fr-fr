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
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053225"
---
# <a name="expected-catch"></a>'catch' attendu
Vous avez utilisé la gestion des exceptions **essayez** bloquer, mais n’avez pas écrit associé **catch** instruction. Le mécanisme de gestion des exceptions requiert que le code peut échouer, ainsi que le code qui ne doit pas s’exécuter si une exception se produit, être encapsulées à l’intérieur d’un **essayez** bloc. Exceptions sont levées à partir la **essayez** bloquer à l’aide de la **lever** instruction et interceptées en dehors de la **essayez** bloc avec un ou plusieurs **catch**instructions.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajouter associé **catch** bloc.  
  
- Essayez d’utiliser un **enfin** bloquer au lieu d’un **catch** bloc.  
  
## <a name="see-also"></a>Voir aussi  
 [try... catch... finally, instruction](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objet Error](../../javascript/reference/error-object-javascript.md)