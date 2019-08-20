---
title: '&lt;valeur&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179313"
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
 facultatif. Type de données de la propriété. Le type peut être l’un des suivants :  
  
- Type de langage ECMAScript figurant dans la spécification ECMAScript 5, comme `Number` et `Object`.  
  
- Objet DOM, comme `HTMLElement`, `Window` et `Document`.  
  
- Fonction constructeur JavaScript.  
  
  `integer`  
  facultatif. Si `type` est `Number`, spécifie si la propriété est un entier. La valeur `true` pour indiquer que la propriété est un entier ; sinon, la valeur est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `domElement`  
  facultatif. Cet attribut est déprécié ; l’attribut `type` a la priorité sur cet attribut. Cet attribut spécifie si la propriété documentée est un élément DOM. La valeur `true` pour spécifier que la propriété est un élément DOM ; sinon, la valeur est `false`. Si le `type` attribut n’est pas défini et `domElement` a la valeur `true`, IntelliSense traite la propriété documentée comme un `HTMLElement` lors de l’exécution de saisie semi-automatique des instructions.  
  
  `mayBeNull`  
  facultatif. Spécifie si la propriété documentée peut être définie sur null. La valeur `true` pour indiquer que la propriété peut être définie à null ; sinon, la valeur est `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementType`  
  facultatif. Si `type` est `Array`, cet attribut spécifie le type des éléments contenus dans le tableau.  
  
  `elementInteger`  
  facultatif. Si `type` est `Array` et que `elementType` est `Number`, cet attribut indique si les éléments contenus dans le tableau sont des entiers. Définissez `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, définissez `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `elementDomElement`  
  facultatif. Cet attribut est déprécié ; l’attribut `elementType` a la priorité sur cet attribut. Si `type` est `Array`, cet attribut indique si les éléments contenus dans le tableau sont des éléments DOM. Définissez `true` pour indiquer que les éléments sont des éléments DOM ; sinon, définissez `false`. Si l’attribut `elementType` n’est pas défini et que `elementDomElement` est défini sur `true`, IntelliSense considère chaque élément du tableau en tant que `HTMLElement` au moment de procéder à la complétion des instructions.  
  
  `elementMayBeNull`  
  facultatif. Si `type` est `Array`, indique si les éléments contenus dans le tableau peuvent être définis sur null. Définissez `true` pour indiquer que les éléments contenus dans le tableau peuvent être définis sur null ; sinon, définissez `false`. La valeur par défaut est `false`. Cet attribut n’est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
  `locid`  
  facultatif. L’identificateur pour les informations de localisation sur la propriété. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans l’élément [\<loc>](../ide/loc-javascript.md).  
  
  `description`  
  facultatif. Description de la propriété.  
  
## <a name="remarks"></a>Remarques  
 Utilisation de propriétés ECMAScript 5 la [ \<Résumé >](../ide/summary-javascript.md) élément.  
  
 Utilisez le `<value>` élément immédiatement avant le `get` ou `set` (fonction).  
  
## <a name="example"></a>Exemples  
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
