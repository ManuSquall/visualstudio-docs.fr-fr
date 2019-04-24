---
title: L’URI à désencoder n’est ne pas un encodage valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8fd8add72d016bc3f2e815f41c29c735505c8817
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108423"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>L'URI à décoder contient un caractère incorrect
Vous avez tenté de décoder un incorrectement formé URI (Uniform Resource Identifier). URI ont une syntaxe spéciale ; la plupart des caractères non alphanumériques doivent être encodés avant de pouvoir être utilisés dans un URI. Vous pouvez utiliser la `encodeURI` et `encodeURIComponent` méthodes pour créer un URI à partir d’un élément normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] chaîne.  
  
 Un URI complet se compose d’une séquence de composants et de séparateurs. Le format général est :  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Les noms figurant entre crochets représentent des composants et le « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Assurez-vous que vous tentez de décoder des URI valides uniquement. Vous ne pouvez décoder normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des chaînes, car ils peuvent contenir des caractères non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)