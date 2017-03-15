---
title: "&lt;var&gt; (JavaScript) | Microsoft Docs"
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
  - "<var>, balise XML JavaScript"
  - "var, balise XML JavaScript"
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie les informations de documentation pour une variable.  
  
## Syntaxe  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>  
  
```  
  
#### Paramètres  
 `type`  
 Optionnel.  Type de données de la variable.  Le type peut être l'un des suivants :  
  
-   Un type de langage ECMAScript présent dans la spécification ECMAScript 5, par exemple `Number` ou `Object`.  
  
-   Un objet DOM, tel que `HTMLElement`, `Window`, et `Document`.  
  
-   Une fonction constructeur JavaScript.  
  
 `integer`  
 Optionnel.  Si le `type` est `Number`, spécifie si la variable est un entier.  Affectez la valeur `true` pour indiquer que la variable est un entier ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `type` est prioritaire sur ce dernier.  Cet attribut spécifie si la variable documenté est un élément DOM.  Affectez la valeur `true` pour spécifier que la variable est un élément DOM ; sinon, affectez `false`.  Si l'attribut `type` n'est pas défini et `domElement` détient la valeur `true`, IntelliSense traite la variable documentée comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `mayBeNull`  
 Optionnel.  Spécifie si la variable documentée peut être définie comme null.  Affectez la valeur `true` pour indiquer que la variable peut être définie comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Optionnel.  Si l'attribut `type` est `Array`, cet attribut précise le type des éléments dans le tableau.  
  
 `elementInteger`  
 Optionnel.  Si le `type` est `Array` et que l' `elementType` est un `Number`, cet attribut spécifie si les éléments du tableau sont des entiers.  Affectez la valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `elementType` est prioritaire sur ce dernier.  Si `type` est `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM.  Affectez la valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, affectez `false`.  Si l'attribut `elementType` n'est pas défini et `elementDomElement` détient la valeur `true`, IntelliSense traite chaque élément du tableau comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `elementMayBeNull`  
 Optionnel.  Si `type` est `Array`, spécifie si les éléments du tableau peuvent être définis comme null.  Affectez la valeur `true` pour indiquer que les éléments du tableau peuvent être définis comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `helpKeyword`  
 Optionnel.  Mot clé pour l'Aide F1.  
  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation sur la variable.  L'identificateur est soit un membre ID soit il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans la balise [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Optionnel.  Description de la variable.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser l'élément `<var>`.  
  
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
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)