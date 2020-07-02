---
title: Quantificateur inattendu (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815329"
---
# <a name="unexpected-quantifier-javascript"></a>Quantificateur inattendu (JavaScript)
Lorsque vous composez votre modèle de recherche d’expression régulière, vous avez créé un élément de modèle avec un facteur de répétition non conforme. Par exemple, le modèle  
  
```js
/^+/  
```  
  
 est non conforme, car l’élément ^ (début de l’entrée) ne peut pas avoir un facteur de répétition. Le tableau suivant répertorie les éléments qui ne peuvent pas avoir de facteurs de répétition.  
  
|Élément|Description|  
|-------------|-----------------|  
|^|Début de l’entrée|  
|$|Fin de l’entrée|  
|\b|Limite de mot|  
|\B|Limite de non-mot|  
|*|Zéro, une ou plusieurs répétitions|  
|+|Une ou plusieurs répétitions|  
|?|Zéro ou une répétition|  
|n|n répétitions|  
|{n,}|n ou plus de répétitions|  
|{n, m}|De n à m répétitions, inclus|  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Vérifiez que votre élément de modèle de recherche contient uniquement des facteurs de répétition légale.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Regular expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe des expressions régulières (JavaScript)](https://msdn.microsoft.com/library/1400241x)