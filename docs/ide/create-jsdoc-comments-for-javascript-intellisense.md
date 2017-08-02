---
title: "Cr&#233;er des commentaires JSDoc pour IntelliSense JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Cr&#233;er des commentaires JSDoc pour IntelliSense JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense dans Visual Studio affiche les informations que vous ajoutez à un script sous forme de commentaires JSDoc standard.  Vous pouvez utiliser des commentaires JSDoc pour fournir des informations sur les éléments de code, tels que les fonctions, les champs et les variables.  
  
## Balises de commentaire JSDoc  
 Les balises de commentaire JSDoc standard suivantes sont utilisées par IntelliSense pour afficher des informations relatives à votre code.  
  
|Balise JSDoc|Syntaxe|Notes|  
|------------------|-------------|-----------|  
|@deprecated|@deprecated *description*|Spécifie une fonction ou méthode déconseillée.|  
|@description|@description *description*|Spécifie la description d'une fonction ou d'une méthode.|  
|@param|@param {*type*} *nomParamètre**description*|Spécifie les informations de paramètre dans une fonction ou méthode.<br /><br /> TypeScript prend également en charge @paramTag.|  
|@property|@property {*type*} *nomPropriété*|Spécifie les informations, y compris une description, pour un champ ou un membre qui est défini sur un objet.|  
|@returns|@returns {*type*}|Spécifie une valeur de retour.<br /><br /> Pour TypeScript, utilisez @returnType au lieu de @returns.|  
|@summary|@summary *description*|Spécifie la description d'une fonction ou d'une méthode \(identique à @description\).|  
|@type|@type {*type*}|Spécifie le type d'une constante ou d'une variable.|  
|@typedef|@typedef {*type*} *nomTypePersonnalisé*|Spécifie un type personnalisé.|  
  
### Exemples  
 L'exemple suivant illustre l'utilisation des balises JSDoc @description, @param et @return pour la fonction `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 Dans l'exemple précédent, IntelliSense affiche la description, le paramètre et la valeur de retour quand vous tapez la parenthèse ouvrante pour `getArea`.  
  
 ![Informations IntelliSense pour une fonction](~/docs/ide/media/js_intellisense_jsdoc_comments.png "JS\_IntelliSense\_JSDoc\_Comments")  
  
 L'exemple suivant indique comment utiliser la balise @typedef avec la balise @property.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 L'exemple suivant illustre l'utilisation des balises JSDoc @type.  Comme le montre cet exemple, l'ajout d'un seul astérisque \(\*\) après les deux astérisques initiaux \(\*\*\) n'est pas obligatoire.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 L'exemple suivant indique comment utiliser la balise JSDoc @deprecated.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```