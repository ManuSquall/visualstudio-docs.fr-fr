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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81a9a42a104adb2a9d9a9aba483e2588d7332868
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203538"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie les informations de documentation pour le résultat d’un appel de fonction ou une méthode.  
  
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
 `type`  
 facultatif. Le type de données de la valeur de retour. Le type peut être l’un des suivants :  
  
- Un langage ECMAScript tapez dans la spécification ECMAScript 5, tel que `Number` et `Object`.  
  
- Objet DOM, comme `HTMLElement`, `Window` et `Document`.  
  
- Fonction constructeur JavaScript.  
  
  `integer`  
  facultatif. Si `type` est `Number`, spécifie si la valeur de retour est un entier. La valeur `true` pour indiquer que la valeur de retour est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `domElement`  
  facultatif. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut spécifie si la valeur de retour documentée est un élément DOM. La valeur `true` pour spécifier que la valeur de retour est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite la valeur de retour documentée comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `mayBeNull`  
  facultatif. Spécifie si la documentation retourne peut avoir la valeur null. La valeur `true` pour indiquer que la valeur de retournée peut être définie à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementType`  
  facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.  
  
  `elementInteger`  
  facultatif. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementDomElement`  
  facultatif. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.  
  
  `elementMayBeNull`  
  facultatif. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `locid`  
  facultatif. L’identificateur pour les informations de localisation sur la valeur de retour. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans la balise [\<loc>](../ide/loc-javascript.md).  
  
  `value`  
  facultatif. Spécifie le code qui doit être évalué pour une utilisation par IntelliSense au lieu du code de fonction lui-même. Par exemple, vous pouvez utiliser cet attribut pour fournir IntelliSense pour les rappels asynchrones, comme un `Promise`. À l’aide de la `value` attribut avec le `<returns>` élément peut améliorer les performances d’IntelliSense en contournant l’exécution de code longs.  
  
  `description`  
  facultatif. Description de la valeur de retour.  
  
## <a name="remarks"></a>Remarques  
 Le `<returns>` élément doit être placé dans le corps de fonction avant les instructions.  
  
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
