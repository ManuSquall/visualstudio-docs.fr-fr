---
title: '&lt;valeur&gt; (JavaScript) | Microsoft Docs'
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
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f88f3ae2e7442549004d2331b4517eb7fa2b5509
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914331"
---
# <a name="ltvaluegt-javascript"></a>&lt;valeur&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie les informations de documentation pour `get` et `set` fonctions pour les propriétés ECMAScript 3.  
  
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
 `type`  
 Facultatif. Le type de données de la propriété. Le type peut être une des opérations suivantes :  
  
- Un type de langage ECMAScript qui se trouve dans la spécification ECMAScript 5, tel que `Number` et `Object`.  
  
- Un modèle DOM de l’objet, tel que `HTMLElement`, `Window`, et `Document`.  
  
- Une fonction de constructeur JavaScript.  
  
  `integer`  
  Facultatif. Si `type` est `Number`, spécifie si la propriété est un entier. La valeur `true` pour indiquer que la propriété est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `domElement`  
  Facultatif. Cet attribut est déconseillé ; le `type` attribut est prioritaire sur cet attribut. Cet attribut spécifie si la propriété documentée est un élément DOM. La valeur `true` pour spécifier que la propriété est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite la propriété documentée comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `mayBeNull`  
  Facultatif. Spécifie si la propriété documentée peut être définie sur null. La valeur `true` pour indiquer que la propriété peut être définie à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementType`  
  Facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments du tableau.  
  
  `elementInteger`  
  Facultatif. Si `type` est `Array` et `elementType` est `Number`, cet attribut spécifie si les éléments du tableau sont des entiers. La valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementDomElement`  
  Facultatif. Cet attribut est déconseillé ; le `elementType` attribut est prioritaire sur cet attribut. Si `type` est `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM. La valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, la valeur est `false`. Si le `elementType` attribut n’est pas défini et `elementDomElement` a la valeur `true`, IntelliSense traite chaque élément dans le tableau comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `elementMayBeNull`  
  Facultatif. Si `type` est `Array`, spécifie si les éléments dans le tableau peuvent être définis sur null. La valeur `true` pour indiquer que les éléments dans le tableau peuvent être définies à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `locid`  
  Facultatif. L’identificateur pour les informations de localisation sur la propriété. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) élément.  
  
  `description`  
  Facultatif. Une description de la propriété.  
  
## <a name="remarks"></a>Notes  
 Utilisation de propriétés ECMAScript 5 la [ \<Résumé >](../ide/summary-javascript.md) élément.  
  
 Utilisez le `<value>` élément immédiatement avant le `get` ou `set` (fonction).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser le `<value>` élément sur un `get` (fonction).  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)



