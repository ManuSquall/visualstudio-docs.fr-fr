---
description: Vous avez tenté de décoder un URI mal formé.
title: L’URI à décoder n’est pas un encodage valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db9d2f89a193ca4542ff5d1ca5ed5c2ae6419f53
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571985"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>L'URI à décoder contient un caractère incorrect
Vous avez tenté de décoder un URI mal formé (Uniform Resource Identifier). Les URI ont une syntaxe spéciale ; la plupart des caractères non alphanumériques doivent être encodés avant de pouvoir être utilisés dans un URI. Vous pouvez utiliser les `encodeURI` `encodeURIComponent` méthodes et pour créer un URI à partir d’une [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] chaîne normale.  
  
 Un URI complet se compose d’une séquence de composants et de séparateurs. Le format général est le suivant :  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Les noms entre crochets pointus représentent des composants, et les caractères «  : », « / », « ; » et «  ? » sont des caractères réservés utilisés comme séparateurs.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que vous essayez de décoder uniquement les URI valides. Vous ne pouvez pas décoder [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des chaînes normales, car elles peuvent contenir des caractères non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction decodeURI](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [Fonction decodeURIComponent](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)
