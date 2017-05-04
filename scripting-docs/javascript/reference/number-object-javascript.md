---
title: "Number, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Number_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number (objet)"
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Number, objet (JavaScript)
Objet qui représente n'importe quel type de nombre.  Tous les nombres JavaScript sont des nombres à virgule flottante 64 bits.  
  
## Syntaxe  
  
```  
  
numObj = new Number(value)  
```  
  
## Paramètres  
 `numObj`  
 Obligatoire.  Nom de la variable à laquelle l'objet `Number` est assigné.  
  
 `value`  
 Obligatoire.  Valeur numérique.  
  
## Notes  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] crée des objets `Number` quand une variable est définie sur une valeur numérique, par exemple `var num = 255.336;`.  Il est rarement nécessaire de créer explicitement des objets `Number`.  
  
 L'objet `Number` possède ses propres propriétés et méthodes, en plus des propriétés et des méthodes héritées d'`Object`.  Dans certains cas, les nombres sont convertis en chaînes, par exemple quand un nombre est ajouté ou concaténé avec une chaîne, ainsi qu'au moyen de la méthode `toString`.  Pour plus d'informations, consultez [Opérateur d'addition \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript a plusieurs constantes numériques.  Pour obtenir la liste complète, consultez [Constantes numériques](../../javascript/reference/number-constants-javascript.md).  
  
## Configuration requise  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Propriétés  
 Le tableau suivant répertorie les propriétés de l'objet `Number` .  
  
|Propriété|Description|  
|---------------|-----------------|  
|[Propriété constructor](../../javascript/reference/constructor-property-object-javascript.md)|Spécifie la fonction qui crée un objet.|  
|[Propriété prototype](../../javascript/reference/prototype-property-object-javascript.md)|Retourne une référence au prototype pour une classe d'objets.|  
  
## Fonctions  
 Le tableau suivant répertorie les fonctions de l'objet `Number` .  
  
|Fonction|Description|  
|--------------|-----------------|  
|[Fonction Number.isFinite](../../javascript/reference/number-isfinite-function-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur est finie.|  
|[Fonction Number.isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur est un entier.|  
|[Fonction Number.isNaN](../../javascript/reference/number-isnan-function-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur est la valeur réservée `NaN` \(pas un nombre\).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Retourne une valeur booléenne qui indique si une valeur peut être représentée en toute sécurité en JavaScript.|  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes de l'objet `Number` .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Méthode hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet possède une propriété du nom spécifié.|  
|[Méthode isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Retourne une valeur booléenne qui indique si un objet existe dans la hiérarchie prototype d'un autre objet.|  
|[Méthode propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Retourne une valeur booléenne qui indique si une propriété spécifiée fait partie d'un objet et si elle est énumérable.|  
|[Méthode toExponential](../../javascript/reference/toexponential-method-number-javascript.md)|Retourne une chaîne contenant un nombre représenté en notation exponentielle.|  
|[Méthode toFixed](../../javascript/reference/tofixed-method-number-javascript.md)|Retourne une chaîne qui représente un nombre en notation à virgule fixe.|  
|[Méthode toLocaleString](../../javascript/reference/tolocalestring-number.md)|Retourne un objet converti en chaîne en fonction des paramètres régionaux actuels.|  
|[Méthode toPrecision](../../javascript/reference/toprecision-method-number-javascript.md)|Retourne une chaîne contenant un nombre qui est représenté soit en notation exponentielle, soit avec une virgule fixe, et a un nombre spécifié de chiffres.|  
|[Méthode toString](../../javascript/reference/tostring-method-object-javascript.md)|Retourne la représentation d'un objet sous forme de chaîne.|  
|[Méthode valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Retourne la valeur primitive de l'objet spécifié.|  
  
## Voir aussi  
 [JavaScript, objets](../../javascript/reference/javascript-objects.md)   
 [Objet Math](../../javascript/reference/math-object-javascript.md)   
 [new, opérateur](../../javascript/reference/new-operator-decrementjavascript.md)