---
title: Créer des commentaires de documentation XML pour JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619548"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Créer des commentaires de documentation XML pour IntelliSense JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les *Commentaires de documentation XML* sont des commentaires JavaScript que vous ajoutez à un script pour fournir des informations sur les éléments de code tels que les fonctions, les champs et les variables. Dans Visual Studio, ces descriptions de texte s’affichent avec IntelliSense lorsque vous référencez la fonction de script.

 Cette rubrique fournit un didacticiel de base sur l’utilisation des commentaires de documentation XML. Pour plus d’informations sur l’utilisation d’autres éléments, tels que [\<var>](../ide/var-javascript.md) et [\<value>](../ide/value-javascript.md) , et pour obtenir des exemples de code supplémentaires, consultez [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md). Pour plus d’informations sur la fourniture d’informations IntelliSense pour un rappel asynchrone tel qu’un `Promise` , consultez [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> Les commentaires de documentation XML sont disponibles uniquement à partir de fichiers, d'assemblys et de services référencés.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Pour créer des commentaires de documentation XML pour une fonction JavaScript

- Dans la fonction, ajoutez [\<summary>](../ide/summary-javascript.md) les [\<param>](../ide/param-javascript.md) éléments, et [\<returns>](../ide/returns-javascript.md) , et faites précéder chaque élément de trois barres obliques (///).

    > [!NOTE]
    > Chaque élément doit se trouver sur une seule ligne.

     L’exemple suivant illustre une fonction JavaScript.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Pour afficher les commentaires de documentation XML, tapez le nom et la parenthèse ouvrante d’une fonction qui est marquée avec des commentaires de documentation XML, comme dans l’exemple suivant :

    ```javascript
    var areaVal = getArea(
    ```

     Lorsque vous tapez la parenthèse ouvrante de la fonction qui contient les commentaires de documentation XML, l’éditeur de code utilise IntelliSense pour afficher les informations définies dans les commentaires de documentation XML.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Pour créer des commentaires de documentation XML pour un champ JavaScript

- Dans une fonction de constructeur ou une définition d’objet, ajoutez un [\<field>](../ide/field-javascript.md) élément précédé de trois barres obliques (///).

     L’exemple suivant illustre l’utilisation de l' `<field>` élément dans une fonction constructeur. Pour obtenir des exemples supplémentaires, consultez [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Pour afficher les commentaires de documentation XML, créez un objet à l’aide du constructeur de fonction qui est marqué avec des commentaires de documentation XML, comme dans l’exemple suivant.

    ```javascript
    var eng = new Engine();
    ```

- Sur la ligne suivante, tapez le nom de l’objet et un point pour afficher les informations IntelliSense pour le champ.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Pour créer des commentaires de documentation XML pour une fonction surchargée

1. Dans la fonction, ajoutez un [\<signature>](../ide/signature-javascript.md) élément pour chaque surcharge. Dans ces éléments, ajoutez d’autres éléments, tels que `<summary>` , `<param>` et `<returns>` , avant chaque élément avec trois barres obliques (///).

     L’exemple suivant montre une fonction JavaScript surchargée. Dans cet exemple, les surcharges diffèrent par le type de paramètre.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Pour afficher les commentaires de documentation XML, tapez le nom et la parenthèse ouvrante de la fonction qui est marquée avec des commentaires de documentation XML, comme dans l’exemple suivant :

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Pour créer des fonctionnalités IntelliSense localisées

1. Créez un fichier XML qui contient des commentaires de documentation au format OpenAjax MessageBundle.

    > [!IMPORTANT]
    > MessageBundle est le format recommandé. Ce format n’est pas pris en charge dans les fichiers Microsoft Ajax ou. winmd. Pour plus d’informations sur l’utilisation de l’autre `VSDoc` format, consultez [\<loc>](../ide/loc-javascript.md) .

     L’exemple suivant montre le contenu d’un fichier side-car qui contient les informations IntelliSense localisées. Il s’agit d’un fichier XML situé dans un dossier propre à la culture, tel que JA. Le dossier doit se trouver au même emplacement que le fichier. js qui contient l' `<loc>` élément. Le nom de fichier du fichier XML doit correspondre au `filename` paramètre spécifié dans l' `<loc>` élément.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. Dans votre fichier. js, ajoutez le code suivant. L' `<loc>` élément doit être déclaré avant tout script et suit les mêmes règles d’utilisation que l' `<reference>` élément. Pour plus d’informations, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. Dans votre fichier. js, ajoutez les éléments de documentation XML et les descriptions par défaut. Définissez les `locid` valeurs d’attribut de façon à ce qu’elles correspondent aux `name` valeurs d’attribut correspondantes du fichier side-car. Les descriptions par défaut seront remplacées par les informations IntelliSense localisées, si elles sont disponibles.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Pour afficher les commentaires de documentation XML, tapez le nom et la parenthèse ouvrante de la fonction, comme dans l’exemple suivant :

    ```javascript
    add(
    ```

## <a name="see-also"></a>Voir aussi
 [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md) [JavaScript IntelliSense](../ide/javascript-intellisense.md) [: procédure pas à pas : JavaScript IntelliSense dans ASP.net](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
