---
title: '&lt;deprecated&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665804"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spécifie une fonction ou méthode déconseillée.

## <a name="syntax"></a>Syntaxe

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Paramètres
 `type` Facultatif. Spécifie si la fonction ou la méthode sera supprimée dans une version ultérieure, ou si la fonction ou la méthode a déjà été supprimée et que son utilisation peut provoquer une erreur. Affectez la valeur `deprecate` pour spécifier que la fonction ou la méthode sera supprimée dans une version ultérieure. Affectez la valeur `remove` pour spécifier que la fonction ou la méthode a déjà été supprimée.

 `locid` Facultatif. Identificateur des informations de localisation concernant la fonction ou la méthode. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans l’élément [\<loc>](../ide/loc-javascript.md).

 `description` Facultatif. Description de la fonction ou de la méthode qui est dépréciée.

## <a name="remarks"></a>Remarques
 Les éléments utilisés pour annoter des fonctions, qui incluent `<deprecated>`, doivent être placés dans le corps de la fonction avant toute instruction. Lorsque vous marquez une fonction comme dépréciée, nous vous recommandons de remplacer son [\<summary >](../ide/summary-javascript.md) élément par l’élément `<deprecated>`.

## <a name="example"></a>Exemples
 Le code suivant montre comment utiliser l’élément `<deprecated>`.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Voir aussi
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)
