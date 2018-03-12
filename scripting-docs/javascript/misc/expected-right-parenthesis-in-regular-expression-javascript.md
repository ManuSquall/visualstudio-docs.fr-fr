---
title: "Attendu &#39;) &#39; dans l’expression régulière (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Attendu &#39;) &#39; dans l’expression régulière (JavaScript)
Vous a tenté de créer une capture d’expression régulière, une assertion ou un groupe, mais n’incluez pas la parenthèse fermante. Parenthèses ont plusieurs utilisations dans les expressions régulières. Ils servent principalement à capturer des sous-expressions pour spécifier des assertions ou pour regrouper les modèles afin que les éléments peuvent être traitées comme une unité unique par *, +, ?, et ainsi de suite.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajouter les parenthèses fermantes plus à droite.  
  
    > [!NOTE]
    >  Si vous souhaitez faire correspondre une parenthèse unique, l’échappement avec une barre oblique inverse - \\(- afin qu’il n’est pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)