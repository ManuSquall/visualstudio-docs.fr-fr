---
title: Attendu ')' dans l’expression régulière (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c344105010e406ef4936fdcca58baffbd610088
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347422"
---
# <a name="expected--in-regular-expression-javascript"></a>')' attendu dans l'expression régulière (JavaScript)
Vous a tenté de créer une capture d’expression régulière, une assertion ou un groupe, mais n’incluez pas la parenthèse fermante. Parenthèses ont plusieurs fonctions dans les expressions régulières. Ils servent principalement à capturer de sous-expressions, pour spécifier des assertions, ou pour regrouper les modèles afin que les éléments peuvent être traités comme une seule unité par *, +, ?, et ainsi de suite.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Ajoutez les parenthèses de fermeture plus à droite.  
  
    > [!NOTE]
    >  Si vous souhaitez faire correspondre une parenthèse unique, l’échappement avec une barre oblique inverse - \\(- afin qu’il n’est pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)