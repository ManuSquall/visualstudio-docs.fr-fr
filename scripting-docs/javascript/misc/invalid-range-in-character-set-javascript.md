---
title: Plage incorrecte dans le caractère défini (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903632"
---
# <a name="invalid-range-in-character-set-javascript"></a>Plage non valide dans le jeu de caractères (JavaScript)
Vous avez tenté de créer une expression régulière avec une plage de jeu de caractère non valide. Jeux de caractères doivent être comprise entre les caractères uniques uniquement, tels qu’a-z ou 0-9. Vous ne pouvez inclure des classes de caractères tels que \w dans un jeu de caractères. Le premier caractère dans la plage doit également figurer avant le deuxième caractère dans la plage. Exemple :  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utiliser des caractères uniques uniquement pour composer votre jeu de caractères d’expression régulière et assurez-vous qu’ils sont dans le bon ordre.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)