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
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759754"
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
 Optionnel. Spécifie si la fonction ou méthode sera supprimée dans une version ultérieure, ou si la fonction ou méthode a déjà été supprimé et que son utilisation peut entraîner une erreur. La valeur `deprecate` pour spécifier que la fonction ou méthode sera supprimée dans une version ultérieure. La valeur `remove` pour spécifier que la fonction ou méthode a déjà été supprimé.  
  
 `locid`  
 Optionnel. L’identificateur pour les informations de localisation sur la fonction ou méthode. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) élément.  
  
 `description`  
 Optionnel. Description de la fonction ou méthode est déconseillée.  
  
## <a name="remarks"></a>Remarques  
 Les éléments utilisés pour annoter des fonctions, qui incluent `<deprecated>`, doit être placé dans le corps de fonction avant les instructions. Lorsque vous marquez une fonction comme déconseillés, nous vous recommandons de remplacer son [ \<Résumé >](../ide/summary-javascript.md) élément avec la `<deprecated>` élément.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le `<deprecated>` élément.  
  
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
