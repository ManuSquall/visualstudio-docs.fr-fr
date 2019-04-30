---
title: Créer des commentaires de Documentation XML pour JavaScript IntelliSense | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90fb5b1c9a388d64e191915bbcbbe3de65f6aa99
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437623"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Créer des commentaires de documentation XML pour IntelliSense JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Commentaires de documentation XML* sont des commentaires JavaScript que vous ajoutez à un script pour fournir des informations sur les éléments de code tels que les fonctions, les champs et les variables. Dans Visual Studio, ces descriptions textuelles sont affichées avec IntelliSense lorsque vous référencez la fonction de script.  
  
 Cette rubrique fournit un didacticiel de base sur l’utilisation de commentaires de documentation XML. Pour plus d’informations sur l’utilisation d’autres éléments, tels que [ \<var >](../ide/var-javascript.md) et [ \<valeur >](../ide/value-javascript.md)et pour des exemples de code supplémentaires, consultez [commentaires de Documentation XML ](../ide/xml-documentation-comments-javascript.md). Pour plus d’informations sur la communication des informations IntelliSense pour un rappel asynchrone comme un `Promise`, consultez [ \<retourne >](../ide/returns-javascript.md).  
  
> [!NOTE]
> Les commentaires de documentation XML sont disponibles uniquement à partir de fichiers, d'assemblys et de services référencés.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Pour créer des commentaires de documentation XML pour une fonction JavaScript  
  
- Dans la fonction, ajoutez [ \<Résumé >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), et [ \<retourne >](../ide/returns-javascript.md) éléments, faisant précéder chaque trois obliques (/ / /).  
  
    > [!NOTE]
    > Chaque élément doit être sur une seule ligne.  
  
     L’exemple suivant montre une fonction JavaScript.  
  
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
  
     Lorsque vous tapez la parenthèse ouvrante de la fonction qui contient les commentaires de documentation XML, l’éditeur de Code utilise la technologie IntelliSense pour afficher les informations qui sont définies dans les commentaires de documentation XML.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Pour créer des commentaires de Documentation XML pour un champ de JavaScript  
  
- Dans une définition de fonction ou un objet constructeur, ajoutez un [ \<champ >](../ide/field-javascript.md) élément précédé par trois barres obliques (/ / /).  
  
     L’exemple suivant illustre l’utilisation de la `<field>` élément dans une fonction constructeur. Pour obtenir des exemples supplémentaires, consultez [ \<champ >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
- Pour afficher les commentaires de documentation XML, créer un objet à l’aide du constructeur de fonction qui est marqué avec des commentaires de documentation XML, comme dans l’exemple suivant.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
- Sur la ligne suivante, tapez le nom de l’objet et une période pour afficher des informations IntelliSense pour le champ.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Pour créer des commentaires de documentation XML pour une fonction surchargée  
  
1. Dans la fonction, ajoutez un [ \<signature >](../ide/signature-javascript.md) élément pour chaque surcharge. Dans ces éléments, ajouter d’autres éléments, tels que `<summary>`, `<param>`, et `<returns>`, précédant chaque élément avec trois barres obliques (/ / /).  
  
     L’exemple suivant montre une fonction surchargée de JavaScript. Dans cet exemple, les surcharges diffèrent par type de paramètre.  
  
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
  
### <a name="to-create-localized-intellisense"></a>Pour créer l’IntelliSense localisée  
  
1. Créer un fichier XML qui a des commentaires de documentation dans le format OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    > MessageBundle est le format recommandé. Ce format n’est pas pris en charge dans Microsoft Ajax ou dans les fichiers .winmd. Pour plus d’informations sur l’utilisation de l’alternative `VSDoc` mettre en forme, consultez [ \<loc >](../ide/loc-javascript.md).  
  
     L’exemple suivant affiche le contenu dans un fichier side-car qui contient les informations IntelliSense localisées. Il s’agit d’un fichier XML qui se trouve dans un dossier spécifique à la culture, tels que JA. Le dossier doit être dans le même emplacement que le fichier .js qui contient le `<loc>` élément. Le nom de fichier du fichier XML doit correspondre à la `filename` paramètre spécifié dans le `<loc>` élément.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2. Dans votre fichier .js, ajoutez le code suivant. Le `<loc>` élément doit être déclaré avant tout script et suit les mêmes règles d’utilisation en tant que le `<reference>` élément. Pour plus d’informations, consultez [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [ \<loc >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3. Dans votre fichier .js, ajoutez les éléments de documentation XML et les descriptions de la valeur par défaut. Définir le `locid` attribut valeurs devant concorder correspondant `name` des valeurs d’attribut à partir du fichier side-car. Les descriptions par défaut seront remplacées par les informations IntelliSense localisées, s’il est disponible.  
  
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
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB : Procédure pas à pas : JavaScript IntelliSense dans ASP.NET](http://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
