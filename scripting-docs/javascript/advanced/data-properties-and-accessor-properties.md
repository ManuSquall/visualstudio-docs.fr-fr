---
title: "Propri&#233;t&#233;s des donn&#233;es et propri&#233;t&#233;s des accesseurs | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propri&#233;t&#233;s des donn&#233;es et propri&#233;t&#233;s des accesseurs
Cette section inclut toutes les informations dont vous êtes susceptible d'avoir besoin sur les propriétés de données et les propriétés d'accesseur.  
  
### Propriétés de données  
 Une *propriété de données* est une propriété qui peut obtenir et définir une valeur.  Les propriétés de données contiennent les propriétés `value` et `writable` dans leurs descripteurs.  
  
 Le tableau suivant répertorie les attributs d'un descripteur de propriété de données.  
  
|Attribut de descripteur de données|Description|Par défaut|  
|----------------------------------------|-----------------|----------------|  
|`value`|Valeur actuelle de la propriété.|`undefined`|  
|`writable`|`true` ou `false`.  Si l'attribut `writable` a la valeur `true`, la valeur de propriété peut être modifiée.|`false`|  
|`enumerable`|`true` ou `false`.  Si l'attribut `enumerable` a la valeur `true`, la propriété peut être énumérée par une instruction `for…in`.|`false`|  
|`configurable`|`true` ou `false`.  Si l'attribut `configurable` a la valeur `true`, les attributs de propriété peuvent être modifiés et la propriété peut être supprimée.|`false`|  
  
 Si le descripteur n'a pas d'attribut `value`, `writable`, `get` ou `set`, et que le nom de propriété spécifié n'existe pas, une propriété de données est ajoutée.  
  
 Lorsque l'attribut `configurable` a la valeur `false` et l'attribut `writable`, la valeur `true`, les attributs `value` et `writable` peuvent être modifiés.  
  
#### Propriétés de données ajoutées sans utilisation de defineProperty  
 Si vous ajoutez une propriété des données sans utiliser les fonctions `Object.defineProperty`, `Object.defineProperties` ou `Object.create`, les attributs `writable`, `enumerable` et `configurable` ont tous des valeurs `true`.  Une fois que la propriété est ajoutée, vous pouvez la modifier à l'aide de la fonction `Object.defineProperty`.  
  
 Vous pouvez ajouter une propriété de données en utilisant les moyens suivants :  
  
-   Un opérateur d'assignation \(\=\), comme dans `obj.color = "white";`  
  
-   Un littéral d'objet, comme dans `obj = { color: "white", height: 5 };`  
  
-   Une fonction de construction, comme décrit dans [Utilisation de constructeurs pour la définition de types](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### Propriétés d'accesseur  
 Une *propriété d'accesseur* appelle une fonction fournie par l'utilisateur chaque fois que la valeur de la propriété est définie ou récupérée.  Le descripteur d'une propriété d'accesseur contient un attribut `get`, un attribut `set` ou les deux.  
  
 Le tableau suivant répertorie les attributs d'un descripteur de propriété d'accesseur.  
  
|Attribut de descripteur d'accesseur|Description|Par défaut|  
|-----------------------------------------|-----------------|----------------|  
|`get`|Fonction qui retourne la valeur de la propriété.  La fonction n'a pas de paramètre.|`undefined`|  
|`set`|Fonction qui définit la valeur de la propriété.  Elle possède un paramètre qui contient la valeur à assigner.|`undefined`|  
|`enumerable`|`true` ou `false`.  Si l'attribut `enumerable` a la valeur `true`, la propriété peut être énumérée par une instruction `for…in`.|`false`|  
|`configurable`|`true` ou `false`.  Si l'attribut `configurable` a la valeur `true`, les attributs de propriété peuvent être modifiés et la propriété peut être supprimée.|`false`|  
  
 Lorsqu'un accesseur `get` n'est pas défini et qu'une tentative d'accès à la valeur de la propriété a lieu, la valeur `undefined` est retournée.  Lorsqu'un accesseur `set` n'est pas défini et qu'une tentative d'assigner une valeur à la propriété d'accesseur a lieu, rien ne se produit.  
  
### Modifications de propriété  
 Si l'objet possède déjà une propriété avec le nom spécifié, les attributs de propriété sont modifiés.  Lorsque vous modifiez la propriété, les attributs qui ne sont pas spécifiés dans le descripteur restent les mêmes.  
  
 Si l'attribut `configurable` d'une propriété existante a la valeur `false`, la seule modification autorisée est le changement de la valeur de l'attribut `writable` de `true` à `false`.  
  
 Vous pouvez changer une propriété de données en une propriété d'accesseur, et vice versa.  Dans ce cas, les attributs `configurable` et `enumerable` qui ne sont pas spécifiés dans le descripteur sont conservés dans la propriété.  Les autres attributs qui ne sont pas spécifiés dans le descripteur sont définis sur leurs valeurs par défaut.  
  
 Vous pouvez définir de façon incrémentielle des propriétés d'accesseur configurables à l'aide de plusieurs appels à la fonction `Object.defineProperty`.  Par exemple, un appel `Object.defineProperty` peut définir uniquement un utilisateur `get`.  Un appel ultérieur sur le même nom de propriété peut définir un accesseur `set`.  La propriété aura ensuite à la fois un accesseur `get` et un accesseur `set`.  
  
 Pour obtenir un objet descripteur qui s'applique à une propriété existante, vous pouvez utiliser la [Object.getOwnPropertyDescriptor, fonction](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Vous pouvez utiliser la [Object.seal, fonction](../../javascript/reference/object-seal-function-javascript.md) et la [Object.freeze, fonction](../../javascript/reference/object-freeze-function-javascript.md) pour empêcher la modification des attributs de propriété.