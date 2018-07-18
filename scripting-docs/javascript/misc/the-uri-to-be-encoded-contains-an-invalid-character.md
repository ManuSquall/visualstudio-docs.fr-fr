---
title: L’URI à coder contient un caractère non valide | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632929"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à coder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne sous la forme d’un URI (Uniform Resource Identifier), mais il contenait des caractères non valides. Bien que la plupart des caractères sont valides dans les chaînes pour être converti en URI, certaines séquences de caractères Unicode sont interdits.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez la chaîne à encoder contient uniquement les séquences Unicode valides. Un URI complet se compose d’une séquence de composants et des séparateurs. Les crochets pointus représentent les composants et les « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs. La forme générale est la suivante :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Fonction encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)