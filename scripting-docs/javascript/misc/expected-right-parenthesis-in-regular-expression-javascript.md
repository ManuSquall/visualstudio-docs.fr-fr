---
title: Attendu ')' dans l’expression régulière (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 5de54ac2a698cd2536dadbf042554cf70502d92b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076683"
---
# <a name="expected--in-regular-expression-javascript"></a>')' attendu dans l'expression régulière (JavaScript)
Vous a tenté de créer une capture d’expression régulière, une assertion ou un groupe, mais n’incluez pas la parenthèse fermante. Parenthèses ont plusieurs fonctions dans les expressions régulières. Ils servent principalement à capturer de sous-expressions, pour spécifier des assertions, ou pour regrouper les modèles afin que les éléments peuvent être traités comme une seule unité par *, +, ?, et ainsi de suite.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez les parenthèses de fermeture plus à droite.  
  
    > [!NOTE]
    >  Si vous souhaitez faire correspondre une parenthèse unique, l’échappement avec une barre oblique inverse - \\(- afin qu’il n’est pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)