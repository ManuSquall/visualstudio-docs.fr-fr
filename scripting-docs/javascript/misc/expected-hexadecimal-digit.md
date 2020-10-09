---
title: Chiffre hexadécimal ATTENDU | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c6be5302c0c4c6565884fa800da7cb9a002d151
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861933"
---
# <a name="expected-hexadecimal-digit"></a>Chiffre hexadécimal attendu
Vous avez créé une séquence d’échappement Unicode incorrecte. Les séquences d’échappement Unicode commencent par \u, suivies exactement de quatre chiffres hexadécimaux (pas plus ni moins). Les chiffres hexadécimaux Unicode ne peuvent contenir que les chiffres 0-9, les lettres majuscules A-F et les lettres minuscules a-f. L’exemple suivant illustre une séquence d’échappement Unicode correctement formée.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Veillez à ce que vos chiffres hexadécimaux Unicode commencent par \u, contient uniquement les chiffres 0-9, les lettres majuscules A-F, les lettres minuscules a-f ; et sont regroupés en quatre chiffres.  
  
    > [!NOTE]
    > Si vous souhaitez utiliser le texte littéral \u dans une chaîne, utilisez deux barres obliques inverses ( \\ \u)-une pour échapper à la première barre oblique inverse.  
  
## <a name="see-also"></a>Voir aussi  
 [Data types](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)