---
title: '&lt;summary&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646847"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie la description d'une fonction ou d'une méthode.

## <a name="syntax"></a>Syntaxe

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Paramètres
 `locid` Facultatif. Identificateur des informations de localisation concernant la fonction ou la méthode. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur dépend du format spécifié dans l' [\<loc>](../ide/loc-javascript.md) élément.

 `description` Facultatif. Description de la fonction ou de la méthode.

## <a name="remarks"></a>Notes
 Les éléments utilisés pour annoter des fonctions, notamment [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) , et [\<returns>](../ide/returns-javascript.md) , doivent être placés dans le corps de la fonction avant toute instruction.

## <a name="example"></a>Exemple
 Le code suivant montre comment utiliser l’élément `<summary>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Voir aussi
 [Commentaires de documentation XML](../ide/xml-documentation-comments-javascript.md)
