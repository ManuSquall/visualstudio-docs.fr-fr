---
title: '&lt;Résumé&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79aeb36e62279dcdafd2adb0143fa70ce2ee0eba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505067"
---
# <a name="ltsummarygt-javascript"></a>&lt;Résumé&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Documentation Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Spécifie la description d'une fonction ou d'une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `locid`  
 Facultatif. L’identificateur pour les informations de localisation sur la fonction ou méthode. L’identificateur est un membre ID ou il correspond à la `name` valeur dans un regroupement de message défini par OpenAjax métadonnées d’attribut. Le type d’identificateur varie selon le format spécifié dans le [ \<loc >](../ide/loc-javascript.md) élément.  
  
 `description`  
 Facultatif. Description de la fonction ou méthode.  
  
## <a name="remarks"></a>Notes  
 Les éléments utilisés pour annoter des fonctions, qui incluent [ \<Résumé >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), et [ \<retourne >](../ide/returns-javascript.md), doit être placé dans le corps de fonction avant les instructions.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le `<summary>` élément.  
  
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
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)



