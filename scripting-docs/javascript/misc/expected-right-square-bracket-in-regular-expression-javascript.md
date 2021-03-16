---
description: Vous avez tenté de créer une classe de caractères pour une correspondance d’expression régulière, mais n’incluait pas le crochet droit.
title: "'] 'Attendu dans l’expression régulière (JavaScript) | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b5e7a25f6fbef3bf87d084b149ee9f356981600
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570945"
---
# <a name="expected--in-regular-expression-javascript"></a>']' attendu dans l'expression régulière (JavaScript)
Vous avez tenté de créer une classe de caractères pour une correspondance d’expression régulière, mais n’incluait pas le crochet droit. Les combinaisons de caractères littéraux individuelles peuvent être assemblées dans des classes de caractères en les plaçant entre crochets. Une classe de caractères correspond à n’importe quel caractère qu’elle contient. Par exemple,/[ABC]/correspond à l’une des lettres « a », « b » ou « c ».  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez le crochet droit à l’expression régulière.  
  
    > [!NOTE]
    > Si vous souhaitez mettre en correspondance un seul crochet, collez-le avec une barre oblique inverse- \\ [-afin qu’il ne soit pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Regular expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Syntaxe des expressions régulières (JavaScript)](/previous-versions/1400241x(v=vs.100))
