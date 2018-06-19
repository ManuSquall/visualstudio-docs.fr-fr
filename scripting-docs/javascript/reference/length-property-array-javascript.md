---
title: Length, propriété (Array) (JavaScript) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637919"
---
# <a name="length-property-array-javascript"></a>length, propriété (Array) (JavaScript)
Obtient ou définit la longueur du tableau. Il s'agit d'un nombre avec une unité de plus que l'élément le plus élevé défini dans un tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>Paramètres  
 `numVar`  
 Obligatoire. N'importe quel nombre.  
  
 `arrayObj`  
 Obligatoire. Tout objet `Array`.  
  
## <a name="remarks"></a>Remarques  
 En JavaScript, les tableaux sont fragmentés et les éléments d'un tableau ne doivent pas être contigus. La propriété `length` n'est pas nécessairement le nombre d'éléments du tableau. Par exemple, dans la définition de tableau suivante, `my_array.length` contient le chiffre 7, et non 2 :  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Si la valeur de la propriété `length` est inférieure à sa valeur précédente, le tableau est tronqué et tous les éléments ayant des index de tableau égaux ou supérieurs à la nouvelle valeur de la propriété `length` sont perdus.  
  
 Si la valeur de la propriété length est supérieure à sa valeur précédente, le tableau est développé et tous les éléments créés ont la valeur `undefined`.  
  
 L'exemple ci-dessous illustre l'utilisation de la propriété `length` :  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  Depuis Internet Explorer 9 (mode normes), les virgules de fin figurant dans l'initialisation d'un tableau sont gérées différemment.