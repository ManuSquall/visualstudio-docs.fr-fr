---
title: Nœuds de filtre | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2789676505588c2041abfd876a228fc456ee3607
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495870"
---
# <a name="filter-nodes"></a>Nœuds de filtre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [filtrer des nœuds](https://docs.microsoft.com/visualstudio/designers/filter-nodes).  
  
Dans le concepteur de nuanceur, les nœuds de filtre transforment une entrée, par exemple, un échantillon de couleur ou de texture, en valeur de couleur figurative. Ces valeurs de couleurs figuratives sont couramment utilisées dans un rendu non photoréaliste ou comme composants dans d’autres effets visuels.  
  
## <a name="filter-node-reference"></a>Informations de référence des nœuds de filtre  
  
|Nœud|Détails|Properties|  
|----------|-------------|----------------|  
|**Flou**|Estompe les pixels d’une texture à l’aide d’une fonction gaussienne.<br /><br /> Vous pouvez l’utiliser pour réduire le détail ou le bruit des couleurs dans une texture.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées de la texture à tester.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Valeur de couleur floue.|**Texture**<br /> Registre de texture associé à l’échantillonneur utilisé lors de la création du flou.|  
|**Désaturer**|Réduit la quantité de couleur dans la couleur spécifiée.<br /><br /> À mesure que vous enlevez de la couleur, la valeur de couleur s’approche de son équivalent dans les nuances de gris.<br /><br /> **Entrée :**<br /><br /> `RGB`: `float3`<br /> Couleur à désaturer.<br /><br /> `Percent`: `float`<br /> Pourcentage de couleur à supprimer, exprimé en valeur normalisée dans la plage [0, 1].<br /><br /> **Sortie :**<br /><br /> `Output`: `float3`<br /> Couleur désaturée.|**Luminance**<br /> Pondérations attribuées aux composants de couleur rouge, vert et bleu.|  
|**Détection des bords**|Détecte les bords d’une texture à l’aide d’un détecteur de contour Canny. Les pixels de contour sont sortis en blanc tandis que les pixels autres que de contour sont sortis en noir.<br /><br /> Vous pouvez l’utiliser pour identifier les bords d’une texture afin de pouvoir utiliser des effets supplémentaires pour traiter les pixels de contour.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées de la texture à tester.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Blanc si la texture se trouve sur un bord ; noir dans le cas contraire.|**Texture**<br /> Registre de texture associé à l’échantillonneur utilisé au cours de la détection des bords.|  
|**Améliorer la netteté**|Améliore la netteté d’une texture.<br /><br /> Vous pouvez l’utiliser pour mettre en évidence les moindres détails d’une texture.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées de la texture à tester.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Valeur de couleur floue.|**Texture**<br /> Registre de texture associé à l’échantillonneur utilisé lors de l’amélioration de la netteté.|



