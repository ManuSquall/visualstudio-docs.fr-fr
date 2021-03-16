---
description: Vous appelez le constructeur de tableau avec un argument qui n’est pas un nombre entier (les nombres entiers se composent de zéro plus le jeu d’entiers positifs).
title: La longueur du tableau doit être un entier positif fini | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 49d3d2985706ad6cfca9b6ac441baa039ccf04af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572115"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>La longueur du tableau doit être un entier positif fini
Vous appelez le constructeur de **tableau** avec un argument qui n’est pas un nombre entier (les nombres entiers se composent de zéro plus le jeu d’entiers positifs).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utilisez des entiers positifs uniquement lors de la création d’un `Array` objet. Si vous souhaitez créer un tableau avec un seul élément qui n’est pas un entier, faites-le dans un processus en deux étapes. Commencez par créer un tableau avec un élément, puis placez la valeur dans le premier élément (Array [0]). Voici un exemple qui génère cette erreur.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     L’exemple suivant illustre la façon correcte de spécifier un tableau avec un seul élément numérique.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Il n’y a aucune limite supérieure pour la taille d’un tableau, autre que la valeur entière maximale (environ 4 milliards).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de tableaux](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
