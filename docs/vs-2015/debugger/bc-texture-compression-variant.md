---
title: Variante de Compression de Texture BC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0758d9eb5a003b0353ceb4fee21996d90685fa5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111231"
---
# <a name="bc-texture-compression-variant"></a>Variante de compression de texture BC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Permet la compression de blocs sur les textures dont le format de pixel est une variation de B8G8R8X8, B8G8R8A8 ou R8G8B8A8.  
  
## <a name="interpretation"></a>Interprétation  
 Les formats de compression de blocs comme BC1, BC2 et BC3 occupent beaucoup moins de mémoire que les formats d'image non compressés et consomment ainsi beaucoup moins de bande passante de mémoire. Par rapport à un format non compressé qui utilise 32 bits par pixel, le format BC1 (connu auparavant sous le nom DXT1) assure une compression de 8:1, tandis que le format BC3 (autrefois appelé DXT5) atteint 4:1. La différence entre BC1 et BC3 est que BC1 ne prend pas en charge le canal alpha, alors que BC3 prend en charge le canal alpha avec compression de blocs. Malgré des rapports de compression élevés, la qualité d'image des textures courantes n'est que faiblement affectée. Cependant, la compression de blocs de certains types de textures (par exemple, celles qui montrent une variation de couleurs importante sur une petite surface) peuvent donner des résultats inacceptables.  
  
 Si vos textures sont adaptées à une compression de blocs et que vous n'avez pas besoin d'une fidélité des couleurs parfaite, utilisez un format de compression de blocs pour réduire l'utilisation de mémoire et moins consommer de bande passante.  
  
## <a name="remarks"></a>Notes  
 Vous compressez les textures en utilisant un format de compression de blocs à chaque appel à `ID3DDevice::CreateTexture2D`, qui est chargé de créer une texture source. Plus précisément, les textures sont compressées quand :  
  
- L'objet `D3D11_TEXTURE2D_DESC` passé dans `pDesc` décrit une ressource de nuanceur qui ne change pas, à savoir :  
  
  - Seul l'indicateur D3D11_BIND_SHADER_RESOURCE du membre BindFlags est défini.  
  
  - Le membre Usage a la valeur D3D11_USAGE_DEFAULT ou D3D11_USAGE_IMMUTABLE.  
  
  - Le membre CPUAccessFlags a la valeur 0 (aucun accès à l'UC).  
  
  - Le membre Count du membre SamplerDesc a la valeur 1 (pas d'anticrénelage MSAA (Multi-Sample Anti-Aliasing)).  
  
- Les données initiales sont fournies à l'appel à `CreateTexture2D`.  
  
  Voici les formats sources pris en charge et leurs formats de compression de blocs.  
  
|Format d'origine (source)|Format compressé (cible)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (anciennement DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (anciennement DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 Si le format de votre texture ne figure pas dans la liste, la texture n'est pas modifiée.  
  
## <a name="restrictions-and-limitations"></a>Restrictions et limitations  
 Parfois, les textures créées avec une variation des formats d'image B8G8R8A8 ou R8G8B8A8 n'utilisent pas réellement le canal alpha, mais la variante n'a aucun moyen de savoir s'il est utilisé ou non. Pour assurer des résultats corrects dans le cas où le canal alpha est utilisé, la variante encode toujours ces formats au format BC3, qui est moins efficace. Vous pouvez aider l'analyse des frames graphiques à mieux identifier le potentiel de rendu de votre application avec cette variante en utilisant une variation du format d'image B8G8R8X8 quand vous n'utilisez pas le canal alpha. La variante pourra ainsi utiliser le format BC1, qui est plus efficace.  
  
## <a name="example"></a>Exemple  
 Cette variante compresse les blocs des textures au moment de l'exécution, avant l'appel à `CreateTexture2D`. Nous déconseillons cette approche pour le code de production, car les textures non compressées consomment plus d'espace disque et cette étape supplémentaire peut accroître sensiblement les temps de chargement dans votre application. De plus, la compression de blocs nécessite des ressources de calcul importantes pour l'encodage. Nous vous recommandons plutôt de compresser vos textures hors connexion en utilisant un éditeur ou un processeur d'images qui fait partie de votre pipeline de génération. Ces approches réduisent les besoins en espace disque, éliminent les surcharges de votre application au moment de l’exécution et autorisent un temps de traitement supérieur pour une qualité d’image optimale.  
  
## <a name="see-also"></a>Voir aussi  
 [Variante de dimensions de la texture moitié/un quart](../debugger/half-quarter-texture-dimensions-variant.md)
