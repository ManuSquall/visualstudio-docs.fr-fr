---
title: Un nombre positif fini doit être assigné à la longueur de tableau | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39f2720efbcd8defffb9d0c77047a50e57939e95
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082345"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Un entier positif fini doit être assigné la longueur du tableau
Lors de la définition du **longueur** propriété d’un existant **tableau** objet, que vous avez spécifié une longueur de tableau qui n’était pas un nombre positif ou zéro. Cette erreur se produit lorsque vous affectez une valeur à la **longueur** propriété d’un `Array` objet qui est un nombre négatif ou une valeur non numérique (`NaN`). Notez que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit automatiquement les nombres fractionnaires en entiers.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Affecter un nombre entier positif à la propriété length. Il n’existe aucune limite supérieure pour la taille d’un tableau, autre que la valeur d’entier maximal (environ 4 milliards). L’exemple suivant illustre la façon correcte de définir la **longueur** propriété d’un **tableau** objet.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)