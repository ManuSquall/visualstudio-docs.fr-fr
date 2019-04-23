---
title: Longueur du tableau doit être un entier positif fini | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31673205a7ca94783985e0249c5664b4bbca6147
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073980"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La longueur du tableau doit être un entier positif fini
Vous appelez le **tableau** constructeur avec un argument qui n’est pas un nombre entier (nombres entiers sont constitués de zéro ainsi que l’ensemble d’entiers positifs).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utiliser des entiers positifs uniquement lorsque vous créez un nouveau `Array` objet. Si vous souhaitez créer un tableau avec un seul élément qui n’est pas un entier, faites-le dans un processus en deux étapes. Commencez par créer un tableau avec un seul élément, puis placer la valeur dans le premier élément (array[0]). Voici un exemple qui génère cette erreur.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     L’exemple suivant montre la façon correcte pour spécifier un tableau avec un seul élément numérique.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Il n’existe aucune limite supérieure pour la taille d’un tableau, autre que la valeur d’entier maximal (environ 4 milliards).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des tableaux](../../javascript/advanced/using-arrays-javascript.md)