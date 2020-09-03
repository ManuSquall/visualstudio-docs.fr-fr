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
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814800"
---
# <a name="unterminated-comment"></a>Commentaire inachevé
Vous avez commencé un bloc de commentaires sur plusieurs lignes, mais vous ne l’avez pas correctement terminé. Les commentaires sur plusieurs lignes commencent par une combinaison « /* » et se terminent par la \* combinaison « / » inverse. Par exemple :  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Veillez à mettre fin aux commentaires sur plusieurs lignes avec « */ ».  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions Comment](../../javascript/reference/comment-statements-javascript.md)