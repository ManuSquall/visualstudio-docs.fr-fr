---
title: Quantificateur inattendu (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 693fdf4091a6f6fdf63c701b63c4355a67ee6fbd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096744"
---
# <a name="unexpected-quantifier-javascript"></a>Quantificateur inattendu (JavaScript)
Lorsque vous composez votre modèle de recherche d’expression régulière, vous avez créé un élément de modèle avec un facteur de répétition non conforme. Par exemple, le modèle  
  
```js
/^+/  
```  
  
 n’est pas conforme, car l’élément ^ (début de l’entrée) ne peut pas avoir un facteur de répétition. Le tableau suivant répertorie les éléments qui ne peut pas avoir des facteurs de répétition.  
  
|Élément|Description|  
|-------------|-----------------|  
|^|Début de l’entrée|  
|$|Fin de l’entrée|  
|\b|Limite de mot|  
|\B|Limite de mot|  
|*|Zéro ou plus de répétitions|  
|+|Un ou plusieurs des répétitions|  
|?|Répétitions de zéro ou un|  
|{n}|répétitions n|  
|{n}|n ou plus de répétitions|  
|{n, m}|De n à m répétitions, inclusives|  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que votre élément de modèle de recherche contient uniquement les facteurs de répétition juridique.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet d’Expression régulière](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntaxe d’Expression régulière (JavaScript)](https://msdn.microsoft.com/library/1400241x)