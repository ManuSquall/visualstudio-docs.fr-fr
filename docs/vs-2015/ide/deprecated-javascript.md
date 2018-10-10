---
title: '&lt;déconseillé&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 220f320eba6231161328a08914848114db7ae02b
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880462"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;déconseillé&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Documentation Visual Studio 2017](/visualstudio/).  
  
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
 Facultatif. Spécifie si la fonction ou méthode sera supprimée dans une version ultérieure, ou si la fonction ou méthode a déjà été supprimé et que son utilisation peut entraîner une erreur. La valeur `deprecate` pour spécifier que la fonction ou méthode sera supprimée dans une version ultérieure. La valeur `remove` pour spécifier que la fonction ou méthode a déjà été supprimé.  
  
 `locid`  
 Facultatif. L’identificateur pour les informations de localisation sur la fonction ou méthode. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) élément.  
  
 `description`  
 Facultatif. Description de la fonction ou méthode est déconseillée.  
  
## <a name="remarks"></a>Notes  
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



