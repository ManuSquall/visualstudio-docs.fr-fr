---
title: Un nombre positif fini doit être assigné à la longueur du tableau | Microsoft Docs
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
ms.openlocfilehash: cff9c8c42199e106cca5f6f2808866e46a26afe2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576063"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>Un entier positif fini doit être assigné la longueur du tableau
Lors de la définition de la propriété **Length** d’un objet **tableau** existant, vous avez spécifié une longueur de tableau qui n’était pas un nombre positif ou zéro. Cette erreur se produit lorsque vous affectez une valeur à la propriété **Length** d’un objet `Array` qui est négatif ou non un nombre (`NaN`). Notez que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convertit automatiquement les nombres fractionnaires en entiers entiers.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Attribuez un nombre entier positif à la propriété Length. Il n’y a aucune limite supérieure pour la taille d’un tableau, autre que la valeur entière maximale (environ 4 milliards). L’exemple suivant illustre la méthode correcte pour définir la propriété **Length** d’un objet **Array** .  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)