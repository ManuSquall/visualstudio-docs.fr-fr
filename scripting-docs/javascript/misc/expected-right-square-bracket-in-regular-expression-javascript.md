---
title: "Attendu &#39;] &#39; dans l’expression régulière (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Attendu &#39;] &#39; dans l’expression régulière (JavaScript)
Vous a tenté de créer une classe de caractères pour une correspondance d’expression régulière, mais n’incluez pas le crochet de droite. Combinaisons de caractères littéraux individuels peuvent être assemblés dans les classes de caractères en les plaçant entre crochets. Une classe de caractères correspond à tout caractère qu’il contient. Par exemple, / [abc] / correspond à l’un des lettres « a », « b » ou « c ».  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez le crochet droit à l’expression régulière.  
  
    > [!NOTE]
    >  Si vous souhaitez faire correspondre un seul crochet, l’échappement avec une barre oblique inverse - \\[, afin qu’il n’est pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)