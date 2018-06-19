---
title: Math.Abs, fonction (JavaScript) | Documents Microsoft
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
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638369"
---
# <a name="mathabs-function-javascript"></a>Math.abs, fonction (JavaScript)
Retourne la valeur absolue d’un nombre (valeur, indépendamment de si elle est positive ou négative). Par exemple, la valeur absolue de -5 est identique à la valeur absolue de 5.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>Paramètres  
 Requis `number` argument est une expression numérique pour laquelle la valeur absolue est nécessaire.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur absolue de la `number` argument.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre l'utilisation de la fonction `abs`.  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [Math (objet)](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Math](../../javascript/reference/math-object-javascript.md)