---
title: L’URI à encoder contient un caractère non valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 310db785041de0beb0ebbba0cdd9b7c356397bc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862386"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à encoder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne en tant qu’URI (Uniform Resource Identifier), mais elle contenait des caractères non valides. Bien que la plupart des caractères soient valides dans les chaînes à convertir en URI, certaines séquences de caractères Unicode ne sont pas autorisées.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que la chaîne à encoder contient uniquement des séquences Unicode valides. Un URI complet se compose d’une séquence de composants et de séparateurs. Les noms entre crochets pointus représentent des composants, et les caractères «  : », « / », « ; » et «  ? » sont des caractères réservés utilisés comme séparateurs. Le format général est le suivant :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [encodeURI, fonction](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [Fonction encodeURIComponent](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)