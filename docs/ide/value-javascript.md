---
title: "&lt;value&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<value>, balise XML JavaScript"
  - "value, balise XML JavaScript"
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie les informations de documentation pour les fonctions `get` et `set` pour ECMAScript 3 propriétés.  
  
## Syntaxe  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### Paramètres  
 `type`  
 Optionnel.  Le type de données de la propriété.  Le type peut être l'un des suivants :  
  
-   Un type de langage ECMAScript présent dans la spécification ECMAScript 5, par exemple `Number` ou `Object`.  
  
-   Un objet DOM, tel que `HTMLElement`, `Window`, ou `Document`.  
  
-   Une fonction constructeur JavaScript.  
  
 `integer`  
 Optionnel.  Si le `type` est `Number`, spécifie si la propriété est un entier.  Affectez la valeur `true` pour indiquer que la propriété est un entier ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `type` est prioritaire sur ce dernier.  Cet attribut spécifie si la propriété documentée est un élément DOM.  Affectez la valeur `true` pour spécifier que la propriété est un élément DOM ; sinon, affectez `false`.  Si l'attribut `type` n'est pas défini et `domElement` détient la valeur `true`, IntelliSense traite la propriété documentée comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `mayBeNull`  
 Optionnel.  Spécifie si la propriété documentée peut être définie comme null.  Affectez la valeur `true` pour indiquer que la propriété peut être définie comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Optionnel.  Si l'attribut `type` est un `Array`, cet attribut précise le type des éléments dans le tableau.  
  
 `elementInteger`  
 Optionnel.  Si le `type` est `Array` et que l' `elementType` est `Number`, cet attribut spécifie si les éléments du tableau sont des entiers.  Affectez la valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `elementType` est prioritaire sur ce dernier.  Si le `type` est un `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM.  Affectez la valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, affectez `false`.  Si l'attribut `elementType` n'est pas défini et `elementDomElement` détient la valeur `true`, IntelliSense traite chaque élément du tableau comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `elementMayBeNull`  
 Optionnel.  Si le `type` est un `Array`, spécifie si les éléments du tableau peuvent être définis comme null.  Affectez la valeur `true` pour indiquer que les éléments du tableau peuvent être définis comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation à propos de la propriété.  L'identificateur est soit un membre ID soit il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans l'élément [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Optionnel.  Une description de la propriété.  
  
## Notes  
 Les propriétés ECMAScript 5 utilisent l'élément [\<summary\>](../ide/summary-javascript.md).  
  
 Utilisez l'élément `<value>` immédiatement avant la fonction `get` ou `set`.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser l' `<value>` élément sur une `get` fonction.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)