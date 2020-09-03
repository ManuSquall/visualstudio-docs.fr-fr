---
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
ms.openlocfilehash: 8a2a2b83b818e37c0b62e103fe284c5c4d110c6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815628"
---
# <a name="expected--in-regular-expression-javascript"></a>']' attendu dans l'expression régulière (JavaScript)
Vous avez tenté de créer une classe de caractères pour une correspondance d’expression régulière, mais n’incluait pas le crochet droit. Les combinaisons de caractères littéraux individuelles peuvent être assemblées dans des classes de caractères en les plaçant entre crochets. Une classe de caractères correspond à n’importe quel caractère qu’elle contient. Par exemple,/[ABC]/correspond à l’une des lettres « a », « b » ou « c ».  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez le crochet droit à l’expression régulière.  
  
    > [!NOTE]
    > Si vous souhaitez mettre en correspondance un seul crochet, collez-le avec une barre oblique inverse- \\ [-afin qu’il ne soit pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Regular expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe des expressions régulières (JavaScript)](https://msdn.microsoft.com/library/1400241x)