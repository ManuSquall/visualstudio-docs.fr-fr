---
title: "Set, méthode (Float32Array) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 0d486ed3-72eb-4af2-b0a6-ae727c588883
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdd3d5b350f44aaf5b96a320e0b447587c07ac22
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-float32array"></a>set, méthode (Float32Array)
Définit une valeur ou un tableau de valeurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
float32Array.set(index, value);  
float32Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Paramètres  
 `index`  
 Index de l'emplacement à définir.  
  
 `value`  
 Valeur à définir.  
  
 `array`  
 Tableau typé ou non typé de valeurs à définir.  
  
 `offset`  
 Index dans le tableau en cours au niveau duquel les valeurs doivent être écrites.  
  
## <a name="remarks"></a>Remarques  
 Si le tableau d'entrée est un TypedArray, les deux tableaux peuvent utiliser le même ArrayBuffer sous-jacent. Dans cette situation, les valeurs sont définies comme si toutes les données étaient d'abord copiées dans une mémoire tampon temporaire qui ne chevauche pas les tableaux, puis les données de la mémoire tampon temporaire étaient copiées dans le tableau en cours.  
  
 Si l'offset plus la longueur du tableau donné sont en dehors des limites du TypedArray en cours, une exception est levée.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment définir le premier élément du tableau.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            floatArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]