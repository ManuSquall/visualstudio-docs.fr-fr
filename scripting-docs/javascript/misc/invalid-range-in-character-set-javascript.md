---
description: Vous avez tenté de créer une expression régulière avec une plage de jeux de caractères non valide.
title: Plage non valide dans le jeu de caractères (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9441f9cfd3adf94ddd38841d522c83922c9154f1
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571673"
---
# <a name="invalid-range-in-character-set-javascript"></a>Plage non valide dans le jeu de caractères (JavaScript)
Vous avez tenté de créer une expression régulière avec une plage de jeux de caractères non valide. Les jeux de caractères doivent être compris entre des caractères simples, par exemple a-z ou 0-9 ; vous ne pouvez pas inclure de classes de caractères telles que \w dans un jeu de caractères. Le premier caractère de la plage doit également précéder le deuxième caractère de la plage. Par exemple :  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utilisez uniquement des caractères uniques pour composer votre jeu de caractères d’expression régulière et assurez-vous qu’ils sont dans le bon ordre.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Regular expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntaxe des expressions régulières (JavaScript)](/previous-versions/1400241x(v=vs.100))
