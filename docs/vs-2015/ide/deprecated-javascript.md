---
title: '&lt;deprecated&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177814"
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
 `type`  
 facultatif. Spécifie si la fonction ou méthode sera supprimée dans une version ultérieure, ou si la fonction ou méthode a déjà été supprimé et que son utilisation peut entraîner une erreur. La valeur `deprecate` pour spécifier que la fonction ou méthode sera supprimée dans une version ultérieure. La valeur `remove` pour spécifier que la fonction ou méthode a déjà été supprimé.  
  
 `locid`  
 facultatif. Identificateur des informations de localisation concernant la fonction ou la méthode. L’identificateur est soit un ID de membre soit il correspond à la valeur d’attribut `name` dans un lot de messages défini par des métadonnées OpenAjax. Le type d’identificateur varie selon le format spécifié dans l’élément [\<loc>](../ide/loc-javascript.md).  
  
 `description`  
 facultatif. Description de la fonction ou méthode est déconseillée.  
  
## <a name="remarks"></a>Remarques  
 Les éléments utilisés pour annoter des fonctions, qui incluent `<deprecated>`, doit être placé dans le corps de fonction avant les instructions. Lorsque vous marquez une fonction comme déconseillés, nous vous recommandons de remplacer son [ \<Résumé >](../ide/summary-javascript.md) élément avec la `<deprecated>` élément.  
  
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
