---
title: Nœuds de filtre
description: En savoir plus sur les nœuds de filtre, qui transforment une entrée comme un échantillon de couleur ou de texture en valeur de couleur figuratives dans le concepteur de nuanceur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97f81a51248f548ea26283dc193645ff7216eb0f
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134163"
---
# <a name="filter-nodes"></a>Nœuds de filtres

Dans le concepteur de nuanceur, les nœuds de filtre transforment une entrée, par exemple, un échantillon de couleur ou de texture, en valeur de couleur figurative. Ces valeurs de couleurs figuratives sont couramment utilisées dans un rendu non photoréaliste ou comme composants dans d’autres effets visuels.

## <a name="filter-node-reference"></a>Informations de référence des nœuds de filtre

|Nœud|Détails|Propriétés|
|----------|-------------|----------------|
|**Flou**|Estompe les pixels d’une texture à l’aide d’une fonction gaussienne.<br /><br /> Vous pouvez l’utiliser pour réduire le détail ou le bruit des couleurs dans une texture.<br /><br /> **Entrée**<br /><br /> `UV`: `float2`<br /> Coordonnées de la texture à tester.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Valeur de couleur floue.|**Texture**<br /> Registre de texture associé à l’échantillonneur utilisé lors de la création du flou.|
|**Désaturer**|Réduit la quantité de couleur dans la couleur spécifiée.<br /><br /> À mesure que vous enlevez de la couleur, la valeur de couleur s’approche de son équivalent dans les nuances de gris.<br /><br /> **Entrée**<br /><br /> `RGB`: `float3`<br /> Couleur à désaturer.<br /><br /> `Percent`: `float`<br /> Pourcentage de couleur à supprimer, exprimé en valeur normalisée dans la plage [0, 1].<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Couleur désaturée.|**Luminance**<br /> Pondérations attribuées aux composants de couleur rouge, vert et bleu.|
|**Détection des bords**|Détecte les bords d’une texture à l’aide d’un détecteur de contour Canny. Les pixels de contour sont sortis en blanc tandis que les pixels autres que de contour sont sortis en noir.<br /><br /> Vous pouvez l’utiliser pour identifier les bords d’une texture afin de pouvoir utiliser des effets supplémentaires pour traiter les pixels de contour.<br /><br /> **Entrée**<br /><br /> `UV`: `float2`<br /> Coordonnées de la texture à tester.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Blanc si la texture se trouve sur un bord ; noir dans le cas contraire.|**Texture**<br /> Registre de texture associé à l’échantillonneur utilisé au cours de la détection des bords.|
|**Améliorer la netteté**|Améliore la netteté d’une texture.<br /><br /> Vous pouvez l’utiliser pour mettre en évidence les moindres détails d’une texture.<br /><br /> **Entrée**<br /><br /> `UV`: `float2`<br /> Coordonnées de la texture à tester.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Valeur de couleur floue.|**Texture**<br /> Registre de texture associé à l’échantillonneur utilisé lors de l’amélioration de la netteté.|