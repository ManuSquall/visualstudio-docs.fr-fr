---
title: Ne peut pas affecter à &#39; cela &#39; | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633159"
---
# <a name="cannot-assign-to-39this39"></a>Ne peut pas affecter à &#39; cela &#39;
Vous avez tenté d’affecter une valeur à **cela**. **Cela** est un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mot clé qui fait référence à :  
  
-   l’objet d’une méthode, en cours d’exécution  
  
-   l’objet global si aucune méthode actuel (ou la méthode n’appartient pas à tout autre objet).  
  
 Une méthode est un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fonction est appelée via un objet. À l’intérieur d’une méthode, le **cela** (mot clé) est une référence à l’objet de la méthode a été appelée par le biais (ce qui se produit à l’objet créé en appelant le constructeur de classe avec le **nouveau** opérateur).  
  
 À l’intérieur d’une méthode, vous pouvez utiliser **cela** pour faire référence à l’objet en cours, mais vous ne pouvez pas affecter une nouvelle valeur à **cela**.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   N’essayez pas d’affecter à **cela**. Pour accéder à une propriété ou méthode d’un objet instancié, utilisez l’opérateur point (par exemple, cercle **.** rayon).  
  
    > [!NOTE]
    >  Impossible de nommer une variable créée par l’utilisateur **cela**; il s’agit d’un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mot réservé.  
  
## <a name="see-also"></a>Voir aussi  
 [Cette instruction](../../javascript/reference/this-statement-javascript.md)   
 [Résolution des problèmes liés aux scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)