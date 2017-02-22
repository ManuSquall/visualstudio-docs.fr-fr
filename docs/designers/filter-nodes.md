---
title: "Nœuds de filtre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 12
---
# Nœuds de filtre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Concepteur Shader, le filtrage des nœuds transforment une entrée, par exemple un échantillon de couleur ou de texture, en une valeur de couleur figurative.  Ces valeurs de couleur figurative sont couramment utilisées dans le rendu non photoréaliste ou en tant que composants dans d'autres effets visuels.  
  
## Référence de nœud de filtre  
  
|Nœud|Détails|Propriétés|  
|----------|-------------|----------------|  
|**Flou**|Floue des pixels dans une texture à l'aide d'une fonction gaussienne.<br /><br /> Vous pouvez l'utiliser pour réduire le détail de la couleur ou le bruit dans une texture.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées du texel à tester.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> La valeur de couleur floutée.|**Texture**<br /> Le registre de textures associé à l'échantillonneur utilisé au cours du floutage.|  
|**Désaturer**|Réduit la quantité de couleur dans la couleur spécifiée.<br /><br /> À mesure que vous enlevez de la couleur, la valeur de couleur s'approche de son équivalent sur l'échelle de gris.<br /><br /> **Entrée :**<br /><br /> `RGB`: `float3`<br /> Couleur à désaturer.<br /><br /> `Percent`: `float`<br /> Le pourcentage de couleur à supprimer, exprimé en valeur normalisée dans la plage \[0, 1\].<br /><br /> **Sortie :**<br /><br /> `Output`: `float3`<br /> Couleur désaturée.|**Luminance**<br /> Pondérations associées aux composants de couleur rouge, vert et bleu.|  
|**Détection des bords**|Détecte le contour d'une texture à l'aide d'un détecteur de contour Canny.  Les pixels de bord sortent vides ; les pixels ne concernant pas les bords sortent en noir.<br /><br /> Vous pouvez l'utiliser pour identifier le contour d'une texture afin que les pixels de contour soient traités avec des effets supplémentaires.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées du texel à tester.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Blanc si le texel est sur un bord ; sinon, noir.|**Texture**<br /> Registre de textures associé à l'échantillonneur utilisé au cours de la détection du contour.|  
|**Améliorer la netteté**|Améliore la netteté d'une texture.<br /><br /> Vous pouvez l'utiliser pour mettre en surbrillance les détails d'une texture.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées du texel à tester.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> La valeur de couleur floutée.|**Texture**<br /> Le registre de textures associé à l'échantillonneur utilisé au cours de l'amélioration de la netteté.|