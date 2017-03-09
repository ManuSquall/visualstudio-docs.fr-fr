---
title: "&lt;returns&gt; (JavaScript) | Microsoft Docs"
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
  - "balise returns XML JavaScript"
  - "<returns>, balise XML JavaScript"
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie les informations de documentation pour le résultat d'un appel de fonction ou de méthode.  
  
## Syntaxe  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### Paramètres  
 `type`  
 Optionnel.  Type de données de la valeur de retour.  Le type peut être l'un des suivants :  
  
-   Un type de langage ECMAScript dans la spécification ECMAScript 5, par exemple `Number` et `Object`.  
  
-   Un objet DOM, tel que `HTMLElement`, `Window`, et `Document`.  
  
-   Une fonction constructeur JavaScript.  
  
 `integer`  
 Optionnel.  Si `type` est `Number`, spécifie que la valeur de retour est un entier.  Affectez la valeur `true` pour indiquer que la valeur de retour est un entier ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `type` est prioritaire sur ce dernier.  Cet attribut spécifie si la valeur de retour documentée est un élément DOM.  Affectez la valeur `true` pour spécifier que la valeur de retour est un élément DOM ; sinon, affectez `false`.  Si l'attribut `type` n'est pas défini et `domElement` détient la valeur `true`, IntelliSense traite la valeur de retour documentée comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `mayBeNull`  
 Optionnel.  Spécifie si la valeur de retour documentée peut être définie comme null.  Affectez la valeur `true` pour indiquer que la valeur de retour peut être définie comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Optionnel.  Si l'attribut `type` est un `Array`, cet attribut précise le type des éléments dans le tableau.  
  
 `elementInteger`  
 Optionnel.  Si `type` est un `Array` et que `elementType` est un `Number`, cet attribut spécifie si les éléments du tableau sont des entiers.  Affectez la valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `elementType` est prioritaire sur ce dernier.  Si le `type` est un `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM.  Affectez la valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, affectez `false`.  Si l'attribut `elementType` n'est pas défini et `elementDomElement` détient la valeur `true`, IntelliSense traite chaque élément du tableau comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `elementMayBeNull`  
 Optionnel.  Si le `type` est un `Array`, spécifie si les éléments du tableau peuvent être définis comme null.  Affecte la valeur `true` pour indiquer que les éléments du tableau peuvent être définis comme null ; sinon, affecte `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation sur la valeur de retour.  L'identificateur est soit un membre ID soit il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans la balise [\<loc\>](../ide/loc-javascript.md).  
  
 `value`  
 Optionnel.  Spécifie le code qui doit être évaluée pour une utilisation par IntelliSense au lieu du code de la fonction lui\-même.  Par exemple, vous pouvez utiliser cet attribut pour fournir à IntelliSense les rappels asynchrones, tels que `Promise`.  L'utilisation de l'attribut `value` avec l'élément `<returns>` peut améliorer les performances IntelliSense en passant une longue exécution de code.  
  
 `description`  
 Optionnel.  Description de la valeur retournée.  
  
## Notes  
 L'élément `<returns>` doit être placé dans le corps de la fonction avant les instructions.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser l'élément `<returns>`.  
  
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
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)