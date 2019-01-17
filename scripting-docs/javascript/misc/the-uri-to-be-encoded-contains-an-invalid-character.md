---
title: L’URI à coder contient un caractère non valide | Microsoft Docs
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
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349788"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>L'URI à coder contient un caractère incorrect
Vous avez tenté d’encoder une chaîne sous la forme d’un URI (Uniform Resource Identifier), mais il contenait des caractères non valides. Bien que la plupart des caractères sont valides dans les chaînes à convertir en URI, certaines séquences de caractères Unicode ne sont pas conformes.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez la chaîne à encoder contient uniquement les séquences Unicode valides. Un URI complet se compose d’une séquence de composants et de séparateurs. Les noms figurant entre crochets représentent des composants et le « : », « / », « ; » et « ? » sont des caractères réservés utilisés comme séparateurs. Le format général est :  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Fonction encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)