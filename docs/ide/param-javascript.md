---
title: "&lt;param&gt; (JavaScript) | Microsoft Docs"
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
  - "<param>, balise XML JavaScript"
  - "balise param XML JavaScript"
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie les informations de documentation pour un paramètre dans une fonction ou une méthode.  
  
## Syntaxe  
  
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
  
#### Paramètres  
 `name`  
 Requis.  Nom du paramètre.  
  
 `type`  
 Optionnel.  Type de données du paramètre.  Le type peut être l'un des suivants :  
  
-   Un type de langage ECMAScript dans la spécification ECMAScript 5, par exemple `Number` et `Object`.  
  
-   Un objet DOM, tel que `HTMLElement`, `Window`, et `Document`.  
  
-   Une fonction constructeur JavaScript.  
  
 `integer`  
 Optionnel.  Si `type` est `Number`, spécifie si le paramètre est un entier.  Affectez la valeur `true` pour indiquer que le paramètre est un entier ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `domElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `type` est prioritaire sur ce dernier.  Cet attribut spécifie si le paramètre documenté est un élément DOM.  Affectez la valeur `true` pour spécifier que le paramètre est un élément DOM ; sinon, affectez `false`.  Si l'attribut `type` n'est pas défini et `domElement` détient la valeur `true`, IntelliSense traite le paramètre documenté comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `mayBeNull`  
 Optionnel.  Spécifie si le paramètre documenté peut être défini comme null.  Affectez la valeur `true` pour indiquer que le paramètre peut être défini comme null ; sinon, affectez `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementType`  
 Optionnel.  Si l'attribut `type` est `Array`, cet attribut précise le type des éléments dans le tableau.  
  
 `elementInteger`  
 Optionnel.  Si `type` est `Array` et que `elementType` est `Number`, cet attribut spécifie si les éléments du tableau sont des entiers.  Affectez la valeur `true` pour indiquer que les éléments du tableau sont des entiers ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `elementDomElement`  
 Optionnel.  Cet attribut est déconseillé ; l'attribut `elementType` est prioritaire sur ce dernier.  Si `type` est `Array`, cet attribut spécifie si les éléments du tableau sont des éléments DOM.  Affectez la valeur `true` pour spécifier que les éléments sont des éléments DOM ; sinon, affectez `false`.  Si l'attribut `elementType` n'est pas défini et `elementDomElement` détient la valeur `true`, IntelliSense traite chaque élément du tableau comme un `HTMLElement` lors de la saisie semi\-automatique des instructions.  
  
 `elementMayBeNull`  
 Optionnel.  Si `type` est `Array`, spécifie si les éléments du tableau peuvent être définis comme null.  Affectez la valeur `true` pour indiquer que les éléments du tableau peuvent être définis comme null ; sinon, affecte `false`.  La valeur par défaut est `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation sur le paramètre.  L'identificateur est soit un ID membre soit il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans l'élément [\<loc\>](../ide/loc-javascript.md).  
  
 `parameterArray`  
 Optionnel.  Précise si le paramètre documenté peut être répété dans l'appel de fonction, tout comme une répétition des paramètres pris en charge dans la fonction `String.format`.  Affectez la valeur `true` pour indiquer que le paramètre peut être répété ; sinon, affectez `false`.  Cet attribut n'est pas utilisé par Visual Studio pour fournir des informations IntelliSense.  
  
 `optional`  
 Optionnel.  Spécifie si le paramètre documenté est facultatif dans l'appel de la fonction.  Affectez la valeur `true` pour indiquer que le paramètre est facultatif ; sinon, affectez `false`.  
  
 `value`  
 Optionnel.  Spécifie le code qui doit être évaluée pour une utilisation par IntelliSense au lieu du code de la fonction lui\-même.  Il est possible d'utiliser cet attribut pour fournir les informations de type lorsque celui\-ci n'est pas défini.  Par exemple, utilisez `value=’1’` pour traiter le type de paramètre comme un nombre.  
  
 `description`  
 Optionnel.  Une description du paramètre.  
  
## Notes  
 Le seul attribut nécessaire est `name`.  Tous les autres attributs sont facultatifs.  
  
 Les éléments utilisés pour annoter des fonctions, tels que [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), et [\<returns\>](../ide/returns-javascript.md), doivent être placés dans le corps de la fonction avant les instructions.  
  
 S'il y a plusieurs éléments `<param>` portant le même nom, l'un des éléments `<param>` est utilisé et les éléments redondants sont ignorés.  Le comportement qui détermine quel élément est utilisé n'est pas défini.  Si `name` fait référence à un paramètre qui n'existe pas, l'élément est ignoré.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser l'élément `<param>`.  
  
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
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)