---
title: "Comment&#160;: cr&#233;er des commentaires de documentation XML JavaScript | Microsoft Docs"
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
  - "commentaires de code, IntelliSense JavaScript"
  - "commentaires de documentation (JavaScript)"
  - "IntelliSense (JavaScript), commentaires de documentation XML"
  - "commentaires de documentation XML, IntelliSense JavaScript"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comment&#160;: cr&#233;er des commentaires de documentation XML JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Commentaires de documentation XML* sont des commentaires JavaScript que vous ajoutez à un script pour fournir des informations sur les éléments de code tels que des fonctions, des champs et variables.  Dans Visual Studio, ces descriptions de texte sont affichées avec IntelliSense lorsque vous faites référence à la fonction de script.  
  
 Cette rubrique fournit un didacticiel de base sur l'utilisation de commentaires de documentation XML.  Pour plus d'informations sur l'utilisation d'autres éléments, tels que [\<var\>](../ide/var-javascript.md) et [\<value\>](../ide/value-javascript.md)et pour des exemples de code supplémentaire, voir [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md).  Pour plus d'informations sur la fourniture d'informations IntelliSense pour un rappel asynchrone comme un `Promise`, voir [\<returns\>](../ide/returns-javascript.md).  
  
> [!NOTE]
>  Commentaires de documentation XML sont disponibles uniquement à partir des services, les assemblys et les fichiers référencés.  
  
### Pour créer des commentaires de documentation XML pour une fonction JavaScript  
  
-   Dans la fonction, ajoutez [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), et [\<returns\>](../ide/returns-javascript.md) des éléments et faites précéder chaque élément avec trois barres transversales \(\/ \/ \/\).  
  
    > [!NOTE]
    >  Chaque élément doit être sur une seule ligne.  
  
     L'exemple suivant montre une fonction JavaScript.  
  
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
  
-   Pour afficher les commentaires de documentation XML, tapez le nom et la parenthèse ouvrante d'une fonction qui est marquée avec les commentaires de documentation XML, comme dans l'exemple suivant :  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Lorsque vous tapez la parenthèse ouvrante de la fonction qui contient les commentaires de documentation XML, l'éditeur de Code utilise IntelliSense pour afficher les informations qui sont définies dans les commentaires de documentation XML.  
  
### Pour créer des commentaires de Documentation XML pour un champ de JavaScript  
  
-   Dans une définition de fonction ou un objet constructeur, ajoutez un [\<field\>](../ide/field-javascript.md) élément précédée par trois barres transversales \(\/ \/ \/\).  
  
     L'exemple suivant illustre l'utilisation de la `<field>` élément dans une fonction constructeur.  Pour obtenir d'autres exemples, consultez [\<field\>](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Pour afficher les commentaires de documentation XML, créez un objet en utilisant le constructeur function qui est marqué avec les commentaires de documentation XML, comme dans l'exemple suivant.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Sur la ligne suivante, tapez le nom de l'objet et une période pour afficher les informations de IntelliSense pour le champ.  
  
    ```javascript  
    eng.  
    ```  
  
### Pour créer des commentaires de documentation XML pour une fonction surchargée  
  
1.  Dans la fonction, ajoutez un [\<signature\>](../ide/signature-javascript.md) élément pour chaque surcharge.  Dans ces éléments, ajouter d'autres éléments, tels que `<summary>`, `<param>`, et `<returns>`, qui précède chaque élément avec trois barres transversales \(\/ \/ \/\).  
  
     L'exemple suivant montre une fonction JavaScript surchargée.  Dans cet exemple, les surcharges diffèrent par type de paramètre.  
  
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
  
2.  Pour afficher les commentaires de documentation XML, tapez le nom et la parenthèse ouvrante de la fonction qui est marquée avec les commentaires de documentation XML, comme dans l'exemple suivant :  
  
    ```javascript  
    calc(  
    ```  
  
### Pour créer des IntelliSense localisée  
  
1.  Créer un fichier XML qui comporte des commentaires de documentation dans le format OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  MessageBundle est le format recommandé.  Ce format n'est pas pris en charge dans Microsoft Ajax ou dans les fichiers .winmd.  Pour plus d'informations sur l'utilisation de l'alternative `VSDoc` de format, consultez [\<loc\>](../ide/loc-javascript.md).  
  
     L'exemple suivant montre contenu dans un fichier annexe qui contient les informations de IntelliSense localisées.  Il s'agit d'un fichier XML qui se trouve dans un dossier spécifique à la culture, comme JA.  Le dossier doit être au même emplacement que le fichier .js qui contient le `<loc>` élément.  Le nom de fichier du fichier XML doit correspondre à la `filename` paramètre spécifié dans la `<loc>` élément.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  Dans votre fichier .js, ajoutez le code suivant.  Le `<loc>` élément doit être déclaré avant tout script et suit les mêmes règles d'utilisation en tant que le `<reference>` élément.  Pour plus d'informations, consultez [IntelliSense JavaScript](../ide/javascript-intellisense.md) et [\<loc\>](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  Dans votre fichier .js, ajoutez les éléments de documentation XML et les descriptions de valeur par défaut.  Définir la `locid` correspondent les valeurs d'attribut `name` les valeurs d'attribut à partir du fichier side\-car.  Les descriptions par défaut seront remplacées par IntelliSense d'informations localisée, s'il est disponible.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Pour afficher les commentaires de documentation XML, tapez le nom et la parenthèse ouvrante de la fonction, comme dans l'exemple suivant :  
  
    ```javascript  
    add(  
    ```  
  
## Voir aussi  
 [IntelliSense JavaScript](../ide/javascript-intellisense.md)   
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/fr-fr/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
