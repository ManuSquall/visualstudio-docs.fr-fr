---
title: '&lt;var&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98bf86f807874fefe066ed2d1008e31451fbbba0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558409"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie les informations de documentation pour une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>   
```  
  
#### <a name="parameters"></a>Paramètres  
 `type`  
 Optionnel. Type de données de la variable. Le type peut être l’un des suivants :  
  
- Type de langage ECMAScript figurant dans la spécification ECMAScript 5, comme `Number` et `Object`.  
  
- Objet DOM, comme `HTMLElement`, `Window` et `Document`.  
  
- Fonction constructeur JavaScript.  
  
  `integer`  
  Optionnel. Si `type` est `Number`, indique si la variable est un entier. Définissez `true` pour indiquer que la variable est un entier ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `domElement`  
  Optionnel. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut indique si la variable documentée est un élément DOM. Définissez `true` pour indiquer que la variable est un élément DOM ; sinon, définissez `false`. Si l’attribut `type` n’est pas défini et que `domElement` est défini sur `true`, IntelliSense considère la variable documentée en tant que `HTMLElement` au moment de procéder à la complétion des instructions.  
  
  `mayBeNull`  
  Optionnel. Indique si la variable documentée peut être définie sur null. Définissez `true` pour indiquer que la variable peut être définie sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementType`  
  Optionnel. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.  
  
  `elementInteger`  
  Optionnel. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementDomElement`  
  Optionnel. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.  
  
  `elementMayBeNull`  
  Optionnel. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `helpKeyword`  
  Optionnel. Mot clé pour l’aide F1.  
  
  `locid`  
  Optionnel. Identificateur des informations de localisation concernant la variable. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans la balise [\<loc>](../ide/loc-javascript.md).  
  
  `description`  
  Optionnel. Description de la variable.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser l'élément `<var>`.  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)
