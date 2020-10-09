---
title: Commentaire inachevé | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8453b05d2d09537f381bd2947dccb6b0a19a6263
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861843"
---
# <a name="unterminated-comment"></a>Commentaire inachevé
Vous avez commencé un bloc de commentaires sur plusieurs lignes, mais vous ne l’avez pas correctement terminé. Les commentaires sur plusieurs lignes commencent par une combinaison « /* » et se terminent par la \* combinaison « / » inverse. Voici un exemple :  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Veillez à mettre fin aux commentaires sur plusieurs lignes avec « */ ».  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions Comment](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)