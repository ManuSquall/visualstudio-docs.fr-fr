---
title: Chiffre hexadécimal attendu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 82f020b5f3b82ab2ce3545102be83a5cd41c6069
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446526"
---
# <a name="expected-hexadecimal-digit"></a>Chiffre hexadécimal attendu
Vous avez créé une séquence d’échappement Unicode incorrecte. Séquences d’échappement Unicode commencent par \u, suivie de quatre chiffres hexadécimaux (plus n’et pas moins). Les chiffres hexadécimaux Unicode peuvent contenir uniquement les chiffres 0-9, les lettres majuscules A-F et les minuscules des lettres a-f. L’exemple suivant montre une séquence d’échappement Unicode correctement formée.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que vos chiffres hexadécimaux Unicode commencent par \u, contient uniquement les nombres 0-9, les lettres majuscules A-F, les minuscules des lettres a-f ; et sont regroupés en quatre chiffres.  
  
    > [!NOTE]
    > Si vous souhaitez utiliser le texte littéral \u dans une chaîne, puis utilisez deux barres obliques inverses - (\\\u)-un à la séquence d’échappement de la première barre oblique inverse.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../javascript/data-types-javascript.md)