---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
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
  - "balise summary XML JavaScript"
  - "<summary>, balise XML JavaScript"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie la description pour une fonction ou une méthode.  
  
## Syntaxe  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### Paramètres  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation sur la fonction ou la méthode.  L'identificateur est soit un membre ID soit il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans l'élément [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Optionnel.  Description de la fonction ou méthode.  
  
## Notes  
 Les éléments utilisés pour annoter des fonctions, qui comprennent [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), et [\<returns\>](../ide/returns-javascript.md), doivent être placés dans le corps de la fonction avant les instructions.  
  
## Exemple  
 Le code suivant montre comment utiliser l'élément `<summary>`.  
  
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
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)