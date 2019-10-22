---
title: L’URI à encoder contient un caractère non valide | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 72fd550e27e64754fe8c4857e9aa4d25ae5711a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572247"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à encoder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne en tant qu’URI (Uniform Resource Identifier), mais elle contenait des caractères non valides. Bien que la plupart des caractères soient valides dans les chaînes à convertir en URI, certaines séquences de caractères Unicode ne sont pas autorisées.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que la chaîne à encoder contient uniquement des séquences Unicode valides. Un URI complet se compose d’une séquence de composants et de séparateurs. Les noms entre crochets pointus représentent des composants, et les caractères «  : », « / », « ; » et «  ? » sont des caractères réservés utilisés comme séparateurs. Le format général est le suivant :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [fonction Encodeuri](../../javascript/reference/encodeuri-function-javascript.md)    
 [Fonction encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)