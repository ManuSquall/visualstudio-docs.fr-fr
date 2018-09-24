---
title: Objet Regular expression attendu | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b8e3c48b116680fe73d4cc318038cb2c13c4164
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280310"
---
# <a name="regular-expression-object-expected"></a>Objet Regular expression attendu
Vous avez tenté d’appeler le **RegExp.prototype.toString** ou **RegExp.prototype.valueOf** méthode sur un objet d’un type autre que `RegExp`. L’objet de ce type d’appel doit être de type `RegExp`.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Appelez le **RegExp.prototype.toString** ou **RegExp.prototype.valueOf** méthodes sur des objets de type `RegExp`.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)