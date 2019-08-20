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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8477de8bf84950d778d4ce843522be35b2d7387
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203760"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie les informations de documentation pour un paramètre dans une fonction ou méthode.  
  
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
 `name`  
 Obligatoire. Nom du paramètre.  
  
 `type`  
 facultatif. Le type de données du paramètre. Le type peut être l’un des suivants :  
  
- Un langage ECMAScript tapez dans la spécification ECMAScript 5, tel que `Number` et `Object`.  
  
- Objet DOM, comme `HTMLElement`, `Window` et `Document`.  
  
- Fonction constructeur JavaScript.  
  
  `integer`  
  facultatif. Si `type` est `Number`, spécifie si le paramètre est un entier. La valeur `true` pour indiquer que le paramètre est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `domElement`  
  facultatif. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut spécifie si le paramètre documenté est un élément DOM. La valeur `true` pour spécifier que le paramètre est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite le paramètre documenté comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `mayBeNull`  
  facultatif. Spécifie si le paramètre documenté peut être défini sur null. La valeur `true` pour indiquer que le paramètre peut être défini à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementType`  
  facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.  
  
  `elementInteger`  
  facultatif. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementDomElement`  
  facultatif. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.  
  
  `elementMayBeNull`  
  facultatif. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `locid`  
  facultatif. L’identificateur pour les informations de localisation sur le paramètre. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans l’élément [\<loc>](../ide/loc-javascript.md).  
  
  `parameterArray`  
  facultatif. Spécifie si le paramètre documenté peut être répété dans l’appel de fonction, similaire à la répétition de paramètres pris en charge dans le `String.format` (fonction). La valeur `true` pour indiquer que le paramètre peut être répété ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `optional`  
  facultatif. Spécifie si le paramètre documenté est facultatif dans la fonction appelante. La valeur `true` pour indiquer que le paramètre est facultatif ; sinon, la valeur est `false`.  
  
  `value`  
  facultatif. Spécifie le code qui doit être évalué pour une utilisation par IntelliSense au lieu du code de fonction lui-même. Vous pouvez utiliser cet attribut est de fournir des informations de type lorsque le type de paramètre n’est pas défini. Par exemple, vous pouvez utiliser `value=’1’` pour traiter le type de paramètre en tant que nombre.  
  
  `description`  
  facultatif. Description du paramètre.  
  
## <a name="remarks"></a>Remarques  
 Le seul attribut requis est `name`. Tous les autres attributs sont facultatifs.  
  
 Éléments utilisés pour annoter des fonctions, telles que [ \<Résumé >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), et [ \<retourne >](../ide/returns-javascript.md), doit être placé. dans le corps de fonction avant les instructions.  
  
 S’il existe plusieurs `<param>` éléments qui ont le même nom, de la `<param>` éléments est utilisée et les éléments redondants sont ignorés. Le comportement qui détermine quel élément est utilisé n’est pas défini. Si `name` fait référence à un paramètre qui n’existe pas, l’élément est ignoré.  
  
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
