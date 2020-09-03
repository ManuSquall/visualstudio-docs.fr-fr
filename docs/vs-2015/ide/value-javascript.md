---
title: '&lt;valeur &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656395"
---
# <a name="ltvaluegt-javascript"></a>&lt;valeur&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie des informations de documentation pour les `get` `set` fonctions et pour les propriétés ECMAScript 3.

## <a name="syntax"></a>Syntaxe

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Paramètres
 `type` Facultatif. Type de données de la propriété. Le type peut être l’un des suivants :

- Type de langage ECMAScript figurant dans la spécification ECMAScript 5, comme `Number` et `Object`.

- Objet DOM, comme `HTMLElement`, `Window` et `Document`.

- Fonction constructeur JavaScript.

  `integer` Facultatif. Si `type` est `Number` , spécifie si la propriété est un entier. Affectez `true` la valeur pour indiquer que la propriété est un entier ; sinon, affectez à la valeur `false` . Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `domElement` Facultatif. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut spécifie si la propriété documentée est un élément DOM. Affectez `true` la valeur pour spécifier que la propriété est un élément DOM ; sinon, affectez à la valeur `false` . Si l' `type` attribut n’est pas défini et que `domElement` a la valeur `true` , IntelliSense traite la propriété documentée en tant que pour `HTMLElement` effectuer la saisie semi-automatique des instructions.

  `mayBeNull` Facultatif. Spécifie si la propriété documentée peut être définie sur null. Affectez `true` la valeur pour indiquer que la propriété peut avoir la valeur NULL ; sinon, affectez à la valeur `false` . La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `elementType` Facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.

  `elementInteger` Facultatif. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `elementDomElement` Facultatif. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.

  `elementMayBeNull` Facultatif. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `locid` Facultatif. Identificateur des informations de localisation sur la propriété. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur dépend du format spécifié dans l' [\<loc>](../ide/loc-javascript.md) élément.

  `description` Facultatif. Une description de la propriété.

## <a name="remarks"></a>Notes
 Les propriétés ECMAScript 5 utilisent l' [\<summary>](../ide/summary-javascript.md) élément.

 Utilisez l' `<value>` élément immédiatement avant la `get` `set` fonction ou.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment utiliser l' `<value>` élément sur une `get` fonction.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Voir aussi
 [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md)
