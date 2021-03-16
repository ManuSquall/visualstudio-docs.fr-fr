---
description: Vous avez inclus une instruction throw dans votre code, mais elle n’a pas été incluse dans un bloc try, ou aucun bloc Catch associé ne peut intercepter l’erreur.
title: Exception levée et non interceptée | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b8abcfced6dfe78dc18f4e31d2bd90d5e5a45a4a
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570633"
---
# <a name="exception-thrown-and-not-caught"></a>Exception levée et non interceptée
Vous avez inclus une `throw` instruction dans votre code, mais elle n’a pas été placée dans un bloc **try** , ou aucun bloc **catch** associé ne peut intercepter l’erreur. Les exceptions sont levées à partir du bloc **try** à l’aide de l’instruction **throw** et interceptées en dehors du bloc **try** avec une instruction **catch** .  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Placez le code qui peut lever une exception dans un bloc **try** et assurez-vous qu’il existe un bloc **catch** correspondant.  
  
- Assurez-vous que votre instruction catch attend la forme correcte de l’exception.  
  
- Si l’exception est levée une nouvelle fois, assurez-vous qu’il existe une autre instruction catch correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Throw (instruction)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [essayer... catch... Finally, instruction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
