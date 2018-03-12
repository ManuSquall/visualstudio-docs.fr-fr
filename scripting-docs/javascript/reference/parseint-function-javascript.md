---
title: parseInt, fonction (JavaScript) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>parseInt, fonction (JavaScript)
Convertit une chaîne en entier.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>Paramètres  
 `numString`  
 Obligatoire. Chaîne à convertir en un nombre.  
  
 `radix`  
 Facultatif. Une valeur comprise entre 2 et 36 qui spécifie la base du nombre figurant dans `numString`. Si cet argument n’est pas fourni, les chaînes comportant un préfixe '0 x' sont considérées comme hexadécimales. Toutes les autres chaînes sont considérées comme nombres décimaux.  
  
## <a name="remarks"></a>Remarques  
 Le `parseInt` fonction retourne une valeur entière égale au nombre contenu dans `numString`. Si aucun préfixe de `numString` peut être analysée en un entier, `NaN` (pas un nombre) est retourné.  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Vous pouvez tester `NaN` à l’aide de la `isNaN` (fonction).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **S’applique aux**: [objet Global](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  À compter de [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], le `parseInt` fonction ne traite pas une chaîne qui a un préfixe « 0 » comme un octal. Lorsque vous n’utilisez pas le `parseInt` de fonction, toutefois, les chaînes avec le préfixe « 0 » peuvent toujours être interprétés comme valeurs octales. Consultez [des Types de données](../../javascript/data-types-javascript.md) pour plus d’informations sur les entiers octales.  
  
## <a name="see-also"></a>Voir aussi  
 [isNaN, fonction](../../javascript/reference/isnan-function-javascript.md)   
 [Fonction parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Objet String](../../javascript/reference/string-object-javascript.md)   
 [Méthode valueOf (Object)](../../javascript/reference/valueof-method-object-javascript.md)