---
title: L’URI à décoder n’est ne pas un encodage valide | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633329"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>L'URI à décoder contient un caractère incorrect
Vous avez tenté de décoder un incorrectement formé URI (Uniform Resource Identifier). URI ont une syntaxe spéciale ; la plupart des caractères non alphanumériques doivent être encodés avant de pouvoir être utilisés dans un URI. Vous pouvez utiliser la `encodeURI` et `encodeURIComponent` méthodes pour créer un URI à partir d’un vecteur normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] chaîne.  
  
 Un URI complet se compose d’une séquence de composants et des séparateurs. La forme générale est la suivante :  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Les crochets pointus représentent les composants et les « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que vous tentez de décoder des URI valides uniquement. Vous ne peut pas décoder normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des chaînes, car ils peuvent contenir des caractères non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [decodeURI, fonction](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)