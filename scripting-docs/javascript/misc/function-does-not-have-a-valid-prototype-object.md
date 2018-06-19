---
title: Fonction n’a pas d’objet prototype valide | Documents Microsoft
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633009"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La fonction ne possède pas d'objet prototype valide
Vous avez tenté d’utiliser **instanceof** pour déterminer si un objet a été dérivé d’une classe de fonction particulière, mais vous redéfini de l’objet `prototype` propriété sous la forme `null`, ou un type d’objet externe (les deux non valide [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objets). Un objet externe peut être un objet à partir du modèle d’objet hôte (par exemple, un document dans Internet Explorer ou objet fenêtre), ou un objet COM externe.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous de la fonction `prototype` propriété fait référence à un élément valide [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Objet de fonction](../../javascript/reference/function-object-javascript.md)   
 [Propriété prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)