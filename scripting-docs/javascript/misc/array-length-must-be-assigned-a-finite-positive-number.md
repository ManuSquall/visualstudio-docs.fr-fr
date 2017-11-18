---
title: "Un nombre positif fini doit être assigné à la longueur de tableau | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63a9d714173334192028b9096de41968befa85ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Un entier positif fini doit être assigné la longueur du tableau
Lors de la définition du **longueur** propriété d’un objet **tableau** objet, que vous avez spécifié une longueur de tableau qui n’est pas un nombre positif ou égal à zéro. Cette erreur se produit lorsque vous affectez une valeur à la **longueur** propriété d’un `Array` objet qui est un nombre négatif ou une valeur non numérique (`NaN`). Notez que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit automatiquement les nombres décimaux en entiers.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Affecter un nombre entier positif pour la propriété de longueur. Il n’existe aucune limite supérieure pour la taille d’un tableau, autre que la valeur entière maximale (environ 4 milliards). L’exemple suivant illustre la façon correcte de définir la **longueur** propriété d’un **tableau** objet.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)