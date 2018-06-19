---
title: Arraybuffer.isview, fonction (ArrayBuffer) | Documents Microsoft
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633369"
---
# <a name="arraybufferisview-function-arraybuffer"></a>ArrayBuffer.isView, fonction (ArrayBuffer)
Détermine si un objet fournit une vue de la mémoire tampon.  
  
## <a name="syntax"></a>Syntaxe  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `object`  
 Obligatoire. Objet à tester.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si l'une ou l'autre des affirmations suivantes est vraie :  
  
-   `object` est un objet `DataView`.  
  
-   `object` es un tableau typé.  
  
 Dans le cas contraire, la méthode retourne `false`.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de la fonction `isView` pour tester un tableau typé et un objet `DataView`.  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)