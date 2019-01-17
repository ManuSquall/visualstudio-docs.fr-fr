---
title: Attendu ']' dans l’expression régulière (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0b34ae4bdf04d261647b9096cda13eec75617c5
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349424"
---
# <a name="expected--in-regular-expression-javascript"></a>']' attendu dans l'expression régulière (JavaScript)
Vous a tenté de créer une classe de caractères pour une correspondance d’expression régulière, mais n’incluez pas le crochet droit. Combinaisons de caractères littérale individuels peuvent être assemblés dans les classes de caractères en les plaçant entre crochets. Une classe de caractères correspond à tout caractère qu’il contient. Par exemple, / [abc] / correspond à l’une des lettres « a », « b » ou « c ».  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez le crochet droit à l’expression régulière.  
  
    > [!NOTE]
    >  Si vous souhaitez faire correspondre un seul crochet, l’échappement avec une barre oblique inverse - \\[, afin qu’il n’est pas interprétée comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)