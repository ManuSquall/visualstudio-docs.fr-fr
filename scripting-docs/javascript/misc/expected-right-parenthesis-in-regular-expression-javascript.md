---
title: "') 'Attendu dans l’expression régulière (JavaScript) | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af32127476c83100c0340021428e3abc572ef2f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815640"
---
# <a name="expected--in-regular-expression-javascript"></a>')' attendu dans l'expression régulière (JavaScript)
Vous avez tenté de créer une capture, une assertion ou un groupe d’expressions régulières, mais n’incluait pas la parenthèse fermante. Les parenthèses ont plusieurs objectifs dans les expressions régulières. Ils sont principalement utilisés pour capturer des sous-expressions, pour spécifier des assertions ou pour regrouper des séquences afin que les éléments puissent être traités comme une seule unité par *, +, ?, et ainsi de suite.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez les parenthèses fermantes les plus à droite.  
  
    > [!NOTE]
    > Si vous souhaitez faire correspondre une seule parenthèse, collez-la avec une barre oblique inverse \\ (-) pour qu’elle ne soit pas interprétée comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Regular expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe des expressions régulières (JavaScript)](https://msdn.microsoft.com/library/1400241x)