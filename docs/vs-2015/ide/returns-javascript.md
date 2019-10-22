---
title: '&lt;returns&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669953"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie des informations de documentation pour le résultat d’un appel de fonction ou de méthode.

## <a name="syntax"></a>Syntaxe

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Paramètres
 `type` Facultatif. Type de données de la valeur de retour. Le type peut être l’un des suivants :

- Type de langage ECMAScript dans la spécification ECMAScript 5, par exemple `Number` et `Object`.

- Objet DOM, comme `HTMLElement`, `Window` et `Document`.

- Fonction constructeur JavaScript.

  `integer` Facultatif. Si `type` est `Number`, spécifie si la valeur de retour est un entier. Affectez la valeur `true` pour indiquer que la valeur de retour est un entier. Sinon, affectez la valeur `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `domElement` Facultatif. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut spécifie si la valeur de retour documentée est un élément DOM. A la valeur `true` pour spécifier que la valeur de retour est un élément DOM ; Sinon, affectez la valeur `false`. Si l’attribut `type` n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite la valeur de retour documentée comme une `HTMLElement` lors de la saisie semi-automatique des instructions.

  `mayBeNull` Facultatif. Spécifie si la valeur de retour documentée peut être définie sur null. Affectez la valeur `true` pour indiquer que la valeur de retour peut être définie sur null. Sinon, affectez la valeur `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `elementType` Facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.

  `elementInteger` Facultatif. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `elementDomElement` Facultatif. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.

  `elementMayBeNull` Facultatif. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `locid` Facultatif. Identificateur des informations de localisation relatives à la valeur de retour. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans la balise [\<loc>](../ide/loc-javascript.md).

  `value` Facultatif. Spécifie le code qui doit être évalué pour être utilisé par IntelliSense au lieu du code de fonction lui-même. Par exemple, vous pouvez utiliser cet attribut pour fournir IntelliSense pour les rappels asynchrones, tels qu’un `Promise`. L’utilisation de l’attribut `value` avec l’élément `<returns>` peut améliorer les performances d’IntelliSense en ignorant l’exécution longue du code.

  `description` Facultatif. Description de la valeur de retour.

## <a name="remarks"></a>Remarques
 L’élément `<returns>` doit être placé dans le corps de la fonction avant toute instruction.

## <a name="example"></a>Exemples
 L’exemple de code suivant montre comment utiliser l'élément `<returns>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Voir aussi
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)
