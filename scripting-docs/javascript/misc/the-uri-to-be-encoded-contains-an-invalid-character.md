---
title: L’URI à coder contient un caractère non valide | Microsoft Docs
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
ms.openlocfilehash: a3c71b90d0711bf317d0ed72d51c0d5d45297c80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841868"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à encoder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne sous la forme d’un URI (Uniform Resource Identifier), mais il contenait des caractères non valides. Bien que la plupart des caractères sont valides dans les chaînes à convertir en URI, certaines séquences de caractères Unicode ne sont pas conformes.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez la chaîne à encoder contient uniquement les séquences Unicode valides. Un URI complet se compose d’une séquence de composants et de séparateurs. Les noms figurant entre crochets représentent des composants et le « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs. Le format général est :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Fonction encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)