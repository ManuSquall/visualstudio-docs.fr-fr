---
title: '&lt;Retourne&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dfe2c3d8e9c91927f7f4d0848b8d180132646614
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501783"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Retourne&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Documentation Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
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
 Facultatif. Le type de données de la valeur de retour. Le type peut être une des opérations suivantes :  
  
-   Un langage ECMAScript tapez dans la spécification ECMAScript 5, tel que `Number` et `Object`.  
  
-   Un modèle DOM de l’objet, tel que `HTMLElement`, `Window`, et `Document`.  
  
-   Une fonction de constructeur JavaScript.  
  
 `integer`  
 Facultatif. Si `type` est `Number`, spécifie si la valeur de retour est un entier. La valeur `true` pour indiquer que la valeur de retour est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Facultatif. Cet attribut est déconseillé ; le `type` attribut est prioritaire sur cet attribut. Cet attribut spécifie si la valeur de retour documentée est un élément DOM. La valeur `true` pour spécifier que la valeur de retour est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite la valeur de retour documentée comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
 `mayBeNull`  
 Facultatif. Spécifie si la documentation retourne peut avoir la valeur null. La valeur `true` pour indiquer que la valeur de retournée peut être définie à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments du tableau.  
  
 `elementInteger`  
 Facultatif. Si `type` est `Array` et `elementType` est `Number`, cet attribut spécifie si les éléments du tableau sont des entiers. La valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Facultatif. Cet attribut est déconseillé ; le `elementType` attribut est prioritaire sur cet attribut. Si `type` est `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM. La valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, la valeur est `false`. Si le `elementType` attribut n’est pas défini et `elementDomElement` a la valeur `true`, IntelliSense traite chaque élément dans le tableau comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
 `elementMayBeNull`  
 Facultatif. Si `type` est `Array`, spécifie si les éléments dans le tableau peuvent être définis sur null. La valeur `true` pour indiquer que les éléments dans le tableau peuvent être définies à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `locid`  
 Facultatif. L’identificateur pour les informations de localisation sur la valeur de retour. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) balise.  
  
 `value`  
 Facultatif. Spécifie le code qui doit être évalué pour une utilisation par IntelliSense au lieu du code de fonction lui-même. Par exemple, vous pouvez utiliser cet attribut pour fournir IntelliSense pour les rappels asynchrones, comme un `Promise`. À l’aide de la `value` attribut avec le `<returns>` élément peut améliorer les performances d’IntelliSense en contournant l’exécution de code longs.  
  
 `description`  
 Facultatif. Description de la valeur de retour.  
  
## <a name="remarks"></a>Notes  
 Le `<returns>` élément doit être placé dans le corps de fonction avant les instructions.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le `<returns>` élément.  
  
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



