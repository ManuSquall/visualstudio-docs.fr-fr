---
title: Créer des commentaires JSDoc pour JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619275"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Créer des commentaires JSDoc pour IntelliSense JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense dans Visual Studio affiche les informations que vous ajoutez à un script sous forme de commentaires JSDoc standard. Vous pouvez utiliser des commentaires JSDoc pour fournir des informations sur les éléments de code, tels que les fonctions, les champs et les variables.

## <a name="jsdoc-comment-tags"></a>Balises de commentaire JSDoc
 Les balises de commentaire JSDoc standard suivantes sont utilisées par IntelliSense pour afficher des informations relatives à votre code.

|  Balise JSDoc   |                       Syntaxe                        |                                                     Notes                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *description*              |                                   Spécifie une fonction ou méthode déconseillée.                                   |
| @description |             @description *description*              |                              Spécifie la description d'une fonction ou d'une méthode.                               |
|    @param    | @param {*type*} *NomParamètre*<em>description</em> | Spécifie les informations de paramètre dans une fonction ou méthode.<br /><br /> La machine à écrire prend également en charge @paramTag. |
|  @property   |          @property {*type*} *NomPropriété*          |   Spécifie les informations, y compris une description, pour un champ ou un membre qui est défini sur un objet.    |
|   @returns   |                  @returns {*type*}                  |           Spécifie une valeur de retour.<br /><br /> Pour la machine à écrire, utilisez @returnType au lieu de @returns.           |
|   @summary   |               @summary *description*                |                   Spécifie la description d’une fonction ou d’une méthode (identique à @description).                   |
|    @type     |                   @type {*type*}                    |                                Spécifie le type d'une constante ou d'une variable.                                |
|   @typedef   |         @typedef {*type*} *NomTypePersonnalisé*          |                                            Spécifie un type personnalisé.                                            |

### <a name="examples"></a>Exemples
 L’exemple suivant illustre l’utilisation des balises @description, @param et @return JSDoc pour une fonction nommée `getArea`.

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

 ![Informations IntelliSense pour une fonction](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 L’exemple suivant montre comment utiliser la balise @typedef avec la balise @property.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 L’exemple suivant illustre l’utilisation des balises @type JSDoc. Comme le montre cet exemple, l’ajout d’un seul astérisque (*) après les deux astérisques initiaux (\*\*) n’est pas obligatoire.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 L’exemple suivant montre comment utiliser la balise @deprecated JSDoc.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
