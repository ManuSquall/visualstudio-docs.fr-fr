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
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816070"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à encoder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne en tant qu’URI (Uniform Resource Identifier), mais elle contenait des caractères non valides. Bien que la plupart des caractères soient valides dans les chaînes à convertir en URI, certaines séquences de caractères Unicode ne sont pas autorisées.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que la chaîne à encoder contient uniquement des séquences Unicode valides. Un URI complet se compose d’une séquence de composants et de séparateurs. Les noms entre crochets pointus représentent des composants, et les caractères «  : », « / », « ; » et «  ? » sont des caractères réservés utilisés comme séparateurs. Le format général est le suivant :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [encodeURI, fonction](../../javascript/reference/encodeuri-function-javascript.md)   
 [Fonction encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)