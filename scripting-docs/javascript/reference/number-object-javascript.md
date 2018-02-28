---
title: "Numéro d’objet (JavaScript) | Documents Microsoft"
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
- Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Number, objet (JavaScript)
Objet qui représente n'importe quel type de nombre. Tous les nombres JavaScript sont des nombres à virgule flottante 64 bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>Paramètres  
 `numObj`  
 Obligatoire. Nom de la variable à laquelle l'objet `Number` est assigné.  
  
 `value`  
 Obligatoire. Valeur numérique.  
  
## <a name="remarks"></a>Remarques  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] crée des objets `Number` quand une variable est définie sur une valeur numérique, par exemple `var num = 255.336;`. Il est rarement nécessaire de créer explicitement des objets `Number`.  
  
 L'objet `Number` possède ses propres propriétés et méthodes, en plus des propriétés et des méthodes héritées d'`Object`. Dans certains cas, les nombres sont convertis en chaînes, par exemple quand un nombre est ajouté ou concaténé avec une chaîne, ainsi qu'au moyen de la méthode `toString`. Pour plus d’informations, consultez [opérateur d’Addition (+)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript a plusieurs constantes numériques. Pour obtenir la liste complète, consultez [constantes de nombre](../../javascript/reference/number-constants-javascript.md).  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Number`.  
  
|Propriété|Description|  
|--------------|-----------------|  
|[constructor, propriété](../../javascript/reference/constructor-property-object-javascript.md)|Spécifie la fonction qui crée un objet.|  
|[prototype, propriété](../../javascript/reference/prototype-property-object-javascript.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## <a name="functions"></a>Fonctions  
 Le tableau suivant répertorie les fonctions de la `Number` objet.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Number.isFinite, fonction](../../javascript/reference/number-isfinite-function-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur est finie.|  
|[Number.isinteger, fonction](../../javascript/reference/number-isinteger-function-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur est un entier.|  
|[Number.IsNaN, fonction](../../javascript/reference/number-isnan-function-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur est la valeur réservée `NaN` (pas un nombre).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur peut être représentée en toute sécurité en JavaScript.|  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes de la `Number` objet.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[isPrototypeOf, méthode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la hiérarchie prototype d'un autre objet.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne indiquant si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[toExponential (méthode)](../../javascript/reference/toexponential-method-number-javascript.md)|Retourne une chaîne contenant un nombre représenté en notation exponentielle.|  
|[toFixed (méthode)](../../javascript/reference/tofixed-method-number-javascript.md)|Retourne une chaîne qui représente un nombre en notation à virgule fixe.|  
|[toLocaleString, méthode](../../javascript/reference/tolocalestring-number.md)|Retourne un objet converti en chaîne en fonction des paramètres régionaux actuels.|  
|[toPrecision (méthode)](../../javascript/reference/toprecision-method-number-javascript.md)|Retourne une chaîne contenant un nombre qui est représenté soit en notation exponentielle, soit avec une virgule fixe, et a un nombre spécifié de chiffres.|  
|[Méthode toString](../../javascript/reference/tostring-method-object-javascript.md)|Retourne la représentation d'un objet sous forme de chaîne.|  
|[Méthode valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets JavaScript](../../javascript/reference/javascript-objects.md)   
 [Math (objet)](../../javascript/reference/math-object-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)