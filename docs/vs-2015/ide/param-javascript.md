---
title: '&lt;param&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670362"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie des informations de documentation pour un paramètre dans une fonction ou une méthode.

## <a name="syntax"></a>Syntaxe

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Paramètres
 `name` Obligatoire. Nom du paramètre.

 `type` Facultatif. Type de données du paramètre. Le type peut être l’un des suivants :

- Type de langage ECMAScript dans la spécification ECMAScript 5, par exemple `Number` et `Object`.

- Objet DOM, comme `HTMLElement`, `Window` et `Document`.

- Fonction constructeur JavaScript.

  `integer` Facultatif. Si `type` est `Number`, spécifie si le paramètre est un entier. Affectez la valeur `true` pour indiquer que le paramètre est un entier. Sinon, affectez la valeur `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `domElement` Facultatif. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut spécifie si le paramètre documenté est un élément DOM. Affectez la valeur `true` pour spécifier que le paramètre est un élément DOM ; Sinon, affectez la valeur `false`. Si l’attribut `type` n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite le paramètre documenté comme une `HTMLElement` lors de la saisie semi-automatique des instructions.

  `mayBeNull` Facultatif. Spécifie si le paramètre documenté peut avoir la valeur null. Affectez la valeur `true` pour indiquer que le paramètre peut avoir la valeur null. Sinon, affectez la valeur `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `elementType` Facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.

  `elementInteger` Facultatif. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `elementDomElement` Facultatif. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.

  `elementMayBeNull` Facultatif. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `locid` Facultatif. Identificateur des informations de localisation concernant le paramètre. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans l’élément [\<loc>](../ide/loc-javascript.md).

  `parameterArray` Facultatif. Spécifie si le paramètre documenté peut être répété dans l’appel de fonction, de la même façon que les paramètres répétitifs pris en charge dans la fonction `String.format`. Affectez la valeur `true` pour indiquer que le paramètre peut être répété. Sinon, affectez la valeur `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.

  `optional` Facultatif. Spécifie si le paramètre documenté est facultatif dans la fonction appelante. Affectez la valeur `true` pour indiquer que le paramètre est facultatif. Sinon, affectez la valeur `false`.

  `value` Facultatif. Spécifie le code qui doit être évalué pour être utilisé par IntelliSense au lieu du code de fonction lui-même. Vous pouvez utiliser cet attribut pour fournir des informations de type lorsque le type de paramètre n’est pas défini. Par exemple, vous pouvez utiliser `value=’1’` pour traiter le type de paramètre comme un nombre.

  `description` Facultatif. Description du paramètre.

## <a name="remarks"></a>Remarques
 Le seul attribut requis est `name`. Tous les autres attributs sont facultatifs.

 Les éléments utilisés pour annoter des fonctions, telles que [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)et [\<returns](../ide/returns-javascript.md)>, doivent être placés dans le corps de la fonction avant toute instruction.

 S’il existe plusieurs éléments `<param>` portant le même nom, l’un des éléments `<param>` est utilisé et les éléments redondants sont ignorés. Le comportement qui détermine l’élément utilisé n’est pas défini. Si `name` fait référence à un paramètre inexistant, l’élément est ignoré.

## <a name="example"></a>Exemples
 L’exemple de code suivant montre comment utiliser l'élément `<param>`.

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

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Voir aussi
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)
