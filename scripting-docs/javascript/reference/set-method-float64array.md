---
title: Set, méthode (Float64Array) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 694965e6-503d-4aaa-8340-63455e96ddf6
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a751319eccff60c7ae47f9eadff41ed22238aa1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639619"
---
# <a name="set-method-float64array"></a>set, méthode (Float64Array)
Définit une valeur ou un tableau de valeurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
float64Array.set(index, value);  
float64Array.set(array, offset);  
  
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
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            floatArr.set(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]