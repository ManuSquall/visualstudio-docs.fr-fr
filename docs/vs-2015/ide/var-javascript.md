---
title: '&lt;var&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a1a8f46f6d5cef0d786110fb27d6ff4c1adce26b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223715"
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
 Facultatif. Le type de données de la variable. Le type peut être une des opérations suivantes :  
  
-   Un type de langage ECMAScript qui se trouve dans la spécification ECMAScript 5, tel que `Number` et `Object`.  
  
-   Un modèle DOM de l’objet, tel que `HTMLElement`, `Window`, et `Document`.  
  
-   Une fonction de constructeur JavaScript.  
  
 `integer`  
 Facultatif. Si `type` est `Number`, spécifie si la variable est un entier. La valeur `true` pour indiquer que la variable est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Facultatif. Cet attribut est déconseillé ; le `type` attribut est prioritaire sur cet attribut. Cet attribut spécifie si la variable documentée est un élément DOM. La valeur `true` pour spécifier que la variable est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite la variable documentée comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
 `mayBeNull`  
 Facultatif. Spécifie si la variable documentée peut être définie sur null. La valeur `true` pour indiquer que la variable peut être définie à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments du tableau.  
  
 `elementInteger`  
 Facultatif. Si `type` est `Array` et `elementType` est `Number`, cet attribut spécifie si les éléments du tableau sont des entiers. La valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Facultatif. Cet attribut est déconseillé ; le `elementType` attribut est prioritaire sur cet attribut. Si `type` est `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM. La valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, la valeur est `false`. Si le `elementType` attribut n’est pas défini et `elementDomElement` a la valeur `true`, IntelliSense traite chaque élément dans le tableau comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
 `elementMayBeNull`  
 Facultatif. Si `type` est `Array`, spécifie si les éléments dans le tableau peuvent être définis sur null. La valeur `true` pour indiquer que les éléments dans le tableau peuvent être définies à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `helpKeyword`  
 Facultatif. Le mot clé d’aide F1.  
  
 `locid`  
 Facultatif. L’identificateur pour la localisation des informations sur la variable. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) balise.  
  
 `description`  
 Facultatif. Une description de la variable.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le `<var>` élément.  
  
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



