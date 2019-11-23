---
title: Exception levée et non interceptée | Microsoft Docs
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572859"
---
# <a name="exception-thrown-and-not-caught"></a>Exception levée et non interceptée
Vous avez inclus une instruction `throw` dans votre code, mais elle n’a pas été placée dans un bloc **try** , ou aucun bloc **catch** associé ne peut intercepter l’erreur. Les exceptions sont levées à partir du bloc **try** à l’aide de l’instruction **throw** et interceptées en dehors du bloc **try** avec une instruction **catch** .  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Placez le code qui peut lever une exception dans un bloc **try** et assurez-vous qu’il existe un bloc **catch** correspondant.  
  
- Assurez-vous que votre instruction catch attend la forme correcte de l’exception.  
  
- Si l’exception est levée une nouvelle fois, assurez-vous qu’il existe une autre instruction catch correspondante.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’erreur](../../javascript/reference/error-object-javascript.md)   
 [instruction throw](../../javascript/reference/throw-statement-javascript.md)   
 [Instruction try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)