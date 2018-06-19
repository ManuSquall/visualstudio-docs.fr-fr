---
title: Propriétés de données et propriétés d’accesseur | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b800131ba76aa432492c0caefdbb9e8d5291924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569469"
---
# <a name="data-properties-and-accessor-properties"></a>Propriétés de données et propriétés d’accesseur
Cette section comprend toutes les informations dont vous pouvez avoir besoin sur les propriétés de données et les propriétés d’accesseur.  
  
### <a name="data-properties"></a>Propriétés de données  
 Une *propriété de données* est une propriété qui peut obtenir et définir une valeur. Le descripteur d’une propriété de données contient les propriétés `value` et `writable`.  
  
 Le tableau suivant répertorie les attributs d’un descripteur de propriété de données.  
  
|Attribut de descripteur de données|Description|Par défaut|  
|-------------------------------|-----------------|-------------|  
|`value`|Valeur actuelle de la propriété.|`undefined`|  
|`writable`|`true` ou `false`. Si `writable` a la valeur `true`, la valeur de propriété peut être modifiée.|`false`|  
|`enumerable`|`true` ou `false`. Si `enumerable` a la valeur `true`, la propriété peut être énumérée par une instruction `for...in`.|`false`|  
|`configurable`|`true` ou `false`. Si `configurable` a la valeur `true`, vous pouvez changer les attributs de propriété et supprimer la propriété.|`false`|  
  
 Si le descripteur n’a pas d’attribut `value`, `writable`, `get` ou `set` et que le nom de propriété spécifié n’existe pas, une propriété de données est ajoutée.  
  
 Quand l’attribut `configurable` a la valeur `false` et que `writable` a la valeur `true`, vous pouvez changer les attributs `value` et `writable`.  
  
#### <a name="data-properties-added-without-using-defineproperty"></a>Propriétés de données ajoutées sans utiliser defineProperty  
 Si vous ajoutez une propriété de données sans utiliser la fonction `Object.defineProperty`, `Object.defineProperties` ou `Object.create`, les attributs `writable`, `enumerable` et `configurable` ont tous la valeur `true`. Une fois que la propriété est ajoutée, vous pouvez le modifier à l’aide de la fonction `Object.defineProperty`.  
  
 Vous pouvez utiliser les méthodes suivantes pour ajouter une propriété de données :  
  
-   Opérateur d’assignation (=), comme dans `obj.color = "white";`  
  
-   Littéral d’objet, comme dans `obj = { color: "white", height: 5 };`  
  
-   Fonction de construction, comme décrit dans [Utilisation de constructeurs pour la définition de types](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### <a name="accessor-properties"></a>Propriétés d’accesseur  
 Une *propriété d’accesseur* appelle une fonction fournie par l’utilisateur chaque fois que la valeur de propriété est définie ou récupérée. Le descripteur d’une propriété d’accesseur contient un attribut `get`, un attribut `set` ou les deux.  
  
 Le tableau suivant répertorie les attributs d’un descripteur de propriété de données.  
  
|Attribut de descripteur de données|Description|Par défaut|  
|-----------------------------------|-----------------|-------------|  
|`get`|Fonction qui retourne la valeur de propriété. La fonction n’a aucun paramètre.|`undefined`|  
|`set`|Fonction qui définit la valeur de propriété. Elle comprend un paramètre qui contient la valeur à affecter.|`undefined`|  
|`enumerable`|`true` ou `false`. Si `enumerable` a la valeur `true`, la propriété peut être énumérée par une instruction `for...in`.|`false`|  
|`configurable`|`true` ou `false`. Si `configurable` a la valeur `true`, vous pouvez changer les attributs de propriété et supprimer la propriété.|`false`|  
  
 Si un accesseur `get` n’est pas défini et qu’une tentative d’accès à la valeur de propriété est effectuée, la valeur `undefined` est retournée. Si un accesseur `set` n’est pas défini et qu’une tentative d’affectation d’une valeur à la propriété d’accesseur est effectuée, rien ne se produit.  
  
### <a name="property-modifications"></a>Modifications de propriété  
 Si l’objet a déjà une propriété portant le nom spécifié, les attributs de propriété sont modifiés. Quand vous modifiez la propriété, les attributs qui ne sont pas spécifiés dans le descripteur restent les mêmes.  
  
 Si l’attribut `configurable` d’une propriété existante a la valeur `false`, vous êtes uniquement autorisé à remplacer la valeur `true` de l’attribut `writable` par la valeur `false`.  
  
 Vous pouvez remplacer une propriété de données par une propriété d’accesseur et vice versa. Dans ce cas, les attributs `configurable` et `enumerable` qui ne sont pas spécifiés dans le descripteur sont conservés dans la propriété. Les autres attributs qui ne sont pas spécifiés dans le descripteur sont définis avec leur valeur par défaut.  
  
 Pour définir de façon incrémentielle des propriétés d’accesseur configurables, effectuez plusieurs appels à la fonction `Object.defineProperty`. Par exemple, un appel à `Object.defineProperty` peut uniquement définir un accesseur `get`. Un appel ultérieur sur le même nom de propriété peut définir un accesseur `set`. La propriété dispose alors de deux accesseurs : `get` et `set`.  
  
 Pour obtenir un objet de descripteur qui s’applique à une propriété existante, vous pouvez utiliser la [fonction Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Vous pouvez utiliser la [fonction Object.Seal](../../javascript/reference/object-seal-function-javascript.md) et la [fonction Object.Freeze](../../javascript/reference/object-freeze-function-javascript.md) pour empêcher toute modification des attributs de propriété.