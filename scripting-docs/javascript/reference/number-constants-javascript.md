---
title: Nombre de constantes (JavaScript) | Documents Microsoft
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
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639199"
---
# <a name="number-constants-javascript"></a>Constantes numériques (JavaScript)
Les constantes de nombre suivantes sont les propriétés de l'objet `Number`.  
  
## <a name="number-object-constants"></a>Constantes d'objet Number  
 Vous n'avez pas besoin de créer un objet `Number` pour accéder à ces constantes.  
  
|Constante|Valeur retournée|  
|--------------|--------------------|  
|`Number.EPSILON`|Le plus petit nombre pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Égal à environ 2.2204460492503130808472633361816E-16.|  
|`Number.MAX_SAFE_INTEGER`|Plus grand nombre pouvant être représenté en toute sécurité en JavaScript. Égal à 9007199254740991.|  
|`Number.MAX_VALUE`|Le plus grand nombre pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Égal à environ 1.79E+308.|  
|`Number.MIN_SAFE_INTEGER`|Plus petit nombre pouvant être représenté en toute sécurité en JavaScript. Égal à-9007199254740991.|  
|`Number.MIN_VALUE`|Le nombre le plus près de zéro pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Égal à environ 5.00E-324.|  
|`Number.NaN`|Valeur qui n'est pas un nombre.<br /><br /> Dans les comparaisons d'égalité, `NaN` n'est égal à aucune valeur, y compris lui-même. Pour tester si une valeur est équivalente à `NaN`, utilisez le [fonction isNaN](../../javascript/reference/isnan-function-javascript.md).|  
|`Number.NEGATIVE_INFINITY`|Valeur inférieure au plus grand nombre négatif pouvant être représentée en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] affiche les valeurs `NEGATIVE_INFINITY` en tant que `-infinity`.|  
|`Number.POSITIVE_INFINITY`|Valeur supérieure au plus grand nombre pouvant être représenté en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] affiche les valeurs `POSITIVE_INFINITY` en tant que `infinity`.|  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 Pour `Number.EPSILON`, `Number.MAX_SAFE_INTEGER` et `Number.MIN_SAFE_INTEGER` :  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **S’applique aux**: [numéro d’objet](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Math, constantes](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript, constantes](../../javascript/reference/javascript-constants.md)   
 [Constante Infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN, constante](../../javascript/reference/nan-constant-javascript.md)   
 [Fonction isNaN](../../javascript/reference/isnan-function-javascript.md)