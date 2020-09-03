---
title: '&lt;signature&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671129"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regroupe un ensemble d’éléments associés pour une fonction ou une méthode afin de fournir de la documentation pour les fonctions surchargées.

## <a name="syntax"></a>Syntaxe

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Paramètres
 `externalid` Facultatif. Si l' `format` attribut de l' [\<loc>](../ide/loc-javascript.md) élément a la valeur `vsdoc` , cet attribut SPÉCIFIe l’ID de membre utilisé pour localiser le code XML associé à la signature. Contrairement `locid` à l’attribut, cet attribut spécifie que tous les éléments du membre qui a cet ID doivent être chargés. Toutes les informations de description associées présentes dans le code XML sont également fusionnées avec les éléments spécifiés dans la signature. Cela vous permet de spécifier des éléments supplémentaires, tels que `<capability>` , dans le fichier side-car sans les spécifier dans le fichier source. `externalid` est un attribut facultatif.

 `externalFile` Facultatif. Spécifie le nom du fichier dans lequel rechercher `externalid` . Cet attribut est ignoré si aucun `externalid` n’est présent. Il s’agit d’un attribut facultatif. La valeur par défaut est le nom du fichier actif, mais avec une extension de fichier. xml au lieu de. js. Par défaut, les règles de recherche de ressources managées pour la localisation sont utilisées pour localiser le fichier.

 `helpKeyword` Facultatif. Mot clé pour l’aide F1.

 `locid` Facultatif. Identificateur des informations de localisation relatives au champ. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur dépend du format spécifié dans la [\<loc>](../ide/loc-javascript.md) balise.

## <a name="remarks"></a>Notes
 Utilisez un `<signature>` élément pour chaque description de fonction surchargée dans le fichier. js, ou utilisez un `<signature>` élément pour chaque ID de membre externe spécifié.

 L' `<signature>` élément doit être placé dans le corps de la fonction avant toute instruction. Quand vous utilisez des [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) éléments, ou [\<returns>](../ide/returns-javascript.md) avec l' `<signature>` élément, placez les autres éléments à l’intérieur du `<signature>` bloc.

## <a name="example"></a>Exemple
 L’exemple de code suivant montre comment utiliser l'élément `<signature>`.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>Voir aussi
 [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md)
