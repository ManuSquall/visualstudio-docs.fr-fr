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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006206"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à encoder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne sous la forme d’un URI (Uniform Resource Identifier), mais il contenait des caractères non valides. Bien que la plupart des caractères sont valides dans les chaînes à convertir en URI, certaines séquences de caractères Unicode ne sont pas conformes.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez la chaîne à encoder contient uniquement les séquences Unicode valides. Un URI complet se compose d’une séquence de composants et de séparateurs. Les noms figurant entre crochets représentent des composants et le « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs. Le format général est :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Fonction encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)