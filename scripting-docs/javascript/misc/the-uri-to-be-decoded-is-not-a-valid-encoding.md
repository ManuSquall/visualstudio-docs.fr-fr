---
title: L’URI à désencoder n’est ne pas un encodage valide | Microsoft Docs
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
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344380"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>L'URI à décoder contient un caractère incorrect
Vous avez tenté de décoder un incorrectement formé URI (Uniform Resource Identifier). URI ont une syntaxe spéciale ; la plupart des caractères non alphanumériques doivent être encodés avant de pouvoir être utilisés dans un URI. Vous pouvez utiliser la `encodeURI` et `encodeURIComponent` méthodes pour créer un URI à partir d’un élément normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] chaîne.  
  
 Un URI complet se compose d’une séquence de composants et de séparateurs. Le format général est :  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Les noms figurant entre crochets représentent des composants et le « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que vous tentez de décoder des URI valides uniquement. Vous ne pouvez décoder normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] des chaînes, car ils peuvent contenir des caractères non valides.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Fonction decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)