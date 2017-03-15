---
title: "&lt;d&#233;conseill&#233;&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;d&#233;conseill&#233;&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spécifie une fonction ou une méthode déconseillée.  
  
## Syntaxe  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### Paramètres  
 `type`  
 Optionnel.  Spécifie si la fonction ou la méthode sera supprimée dans une version ultérieure, ou si la fonction ou la méthode a déjà été supprimée et que son utilisation peut provoquer une erreur.  Affectez la valeur `deprecate` pour spécifier que la fonction ou la méthode sera supprimée dans une version ultérieure.  Affectez la valeur `remove` pour spécifier que la fonction ou la méthode a déjà été supprimée.  
  
 `locid`  
 Optionnel.  L'identificateur pour les informations de localisation sur la fonction ou la méthode.  L'identificateur est ou un ID membre ou il correspond à la valeur d'attribut `name` dans un paquet de message défini par les métadonnées d'OpenAjax.  Le type d'identificateur dépend du format spécifié dans l'élément [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Optionnel.  Description de la fonction ou méthode qui est déconseillée.  
  
## Notes  
 Les éléments utilisés pour annoter les fonctions, notamment `<deprecated>`, doivent être placés dans le corps de la fonction avant les instructions.  Lorsque vous marquez une fonction comme déconseillée, nous recommandons vous remplacez son élément [\<summary\>](../ide/summary-javascript.md) avec l'élément `<deprecated>`.  
  
## Exemple  
 Le code suivant indique comment utiliser l'élément `<deprecated>`.  
  
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
  
## Voir aussi  
 [Commentaires sur la documentation XML](../ide/xml-documentation-comments-javascript.md)